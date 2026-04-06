# 0FFL1N3 R3DA<+0R — Offline Redactor

> AI-powered document redaction that runs entirely on your machine. No cloud. No telemetry. No data leaves your device.

**Built by Tan Sze Yao**

---

## Overview

Offline Redactor is a privacy-first document redaction tool for legal contracts and sensitive documents. It uses Microsoft Presidio and spaCy to automatically detect personally identifiable information (PII), presents every finding for human review, and applies permanent redactions — all without an internet connection after the initial setup.

The redacted output can then be safely uploaded to AI contract analysis tools or shared with third parties.

---

## Features

- **Fully offline** — runs locally via Streamlit; no document data is ever transmitted
- **AI-powered PII detection** — Microsoft Presidio + spaCy `en_core_web_lg` with confidence scores
- **Human-in-the-loop review** — approve or reject each proposed redaction individually
- **Manual phrase redaction** — add custom identifiers the AI may not recognise
- **Draw-to-redact** — drag black boxes directly over PDF pages (signatures, stamps, images)
- **Multi-format support** — PDF, DOCX, and TXT files
- **Colour-coded preview** — each entity type highlighted in a distinct colour before committing
- **BERT NER (optional)** — toggle on `dslim/bert-base-NER` for deeper coverage of unusual names and organisations
- **Instant local download** — redacted file produced in memory; never written to a server

---

## Detected Entity Types

| Category | Entities |
|---|---|
| Identity | `PERSON`, `ORGANIZATION`, `LOCATION` |
| Contact | `PHONE_NUMBER`, `EMAIL_ADDRESS`, `ADDRESS` |
| Financial | `CREDIT_CARD`, `BANK_ROUTING`, `EIN` |
| Government IDs | `US_SSN`, `NRIC_SG`, `CONTRACT_ID` |
| Other | `DATE_TIME`, `IP_ADDRESS`, custom phrases |

---

## Requirements

- Windows 10 or 11 (64-bit)
- Python 3.10, 3.11, or 3.12 — from [python.org](https://www.python.org/downloads/), with **"Add Python to PATH"** ticked
- ~1.5 GB free disk space (Python environment + spaCy model)
- Internet access during first-time setup only
- Any modern browser (Chrome, Edge, Firefox)

---

## Installation

1. Download and unzip `OfflineRedactor.zip`
2. Run `setup.bat` — creates a virtual environment and installs all dependencies (~5 minutes)
3. Run `run.bat` — launches the app and opens it in your browser at `http://localhost:8501`

> `setup.bat` only needs to be run once. Use `run.bat` every time after that.

---

## Usage

1. **Upload** a PDF, DOCX, or TXT contract
2. **Review** the AI-proposed redactions in the sidebar — approve, reject, or add manual phrases
3. **Preview** highlighted entities in the document viewer, page by page
4. **Draw** additional black boxes over any area (signatures, stamps, images) using drawing mode
5. **Apply** redactions and download the clean file

---

## Tech Stack

| Component | Library |
|---|---|
| NLP / PII detection | [Microsoft Presidio](https://github.com/microsoft/presidio) + [spaCy](https://spacy.io/) |
| Optional NER | [HuggingFace Transformers](https://huggingface.co/dslim/bert-base-NER) |
| PDF rendering & redaction | [PyMuPDF (fitz)](https://pymupdf.readthedocs.io/) |
| DOCX handling | [python-docx](https://python-docx.readthedocs.io/) + [mammoth](https://github.com/mwilliamson/python-mammoth) |
| UI | [Streamlit](https://streamlit.io/) |

---

## Project Structure

```
OfflineRedactor/
├── setup.bat                        # First-time setup script
├── run.bat                          # App launcher
├── index.html                       # Landing page (GitHub Pages)
└── contract-redactor/
    ├── app.py                       # Main Streamlit application
    ├── redactor.py                  # Presidio-based redaction engine
    ├── file_handler.py              # PDF / DOCX / TXT read & write
    ├── custom_recognizers.py        # Custom Presidio entity recognizers
    ├── requirements.txt             # Python dependencies
    ├── assets/
    │   ├── banner.gif               # Animated title banner
    │   └── fonts/                   # Share Tech Mono font files
    ├── drawing_component/           # Custom Streamlit canvas component
    │   └── index.html
    └── entity_list_component/       # Custom Streamlit entity list component
        └── index.html
```

---

## License

This project is for personal and internal use. Attribution required if redistributed.

---

*Powered by Microsoft Presidio · spaCy · PyMuPDF · Streamlit*
