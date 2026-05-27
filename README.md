# signal-scanner

A Python-based intelligence pipeline that automates pre-trade screening for institutional digital asset sales. By analyzing raw SEC EDGAR filings, this tool scores institutional funds based on their regulatory footprint, signaling intent to allocate and identifying mandate flexibility (IPS constraints).

# How It Works
This tool uses the public SEC EDGAR API to generate a unified intelligence profile and rank leads via an algorithmic scoring system.

13F Crypto Exposure (+60 points): The tool bypasses basic XML summaries and scrapes the raw text of a fund's recent 13F-HR filings. If it finds the CUSIPs of major spot Bitcoin ETFs (e.g., IBIT, FBTC), the fund is flagged as an active allocator (Tier 1).

IPS Mandate Scanning (+10 to +20 points): The tool deep-scans the raw text of a fund's recent prospectuses, Form ADVs, and general disclosures. If it detects keywords like "digital asset," "cryptocurrency," or "blockchain," it signals that the fund has likely updated its mandate to permit crypto strategies, making them a prime target (Tier 2) even if they haven't bought an ETF yet.

# Output
The scanner produces three deliverables:

A live terminal feed detailing the deep-scan status of each fund.

A formatted intelligence report table.

A color-coded pipeline visualization ranking funds as Tier 1 (Hot), Tier 2 (Warm/Flexible), or Tier 3 (Cold).

# How to Use It
This pipeline requires zero paid API keys and relies entirely on public regulatory data.

Option 1: Run Locally (Terminal)
To run the scanner on your own machine:

Clone this repository to your local drive.

Install the necessary data libraries:

Bash
pip install -r requirements.txt
Open screener.py and ensure the HEADERS variable contains a valid email address (required by the SEC API to prevent rate-limiting).

Run the engine:

Bash
python screener.py
When prompted, enter a target CIK number (e.g., 0001364742 for BlackRock) or leave it blank to run the default institutional test matrix.

Option 2: Run in Google Colab (Zero-Setup)
If you want to run the pipeline without installing Python locally:

Open Google Colab.

Copy the contents of screener.py into a new cell.

Run the cell. The interactive prompt and visual bar chart will render directly inside your browser.
