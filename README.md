# EduGenie - Google Gemini Powered Learning Assistant

EduGenie is a FastAPI-based educational assistant implementing the project described in the supplied documentation.

## Features

- Ask academic questions with Gemini
- Explain concepts using LaMini-Flan-T5
- Generate exactly 3 MCQs with 4 options
- Summarize educational text
- Generate beginner-to-advanced learning paths
- Simple responsive HTML/CSS frontend
- REST endpoints:
  - `/qa`
  - `/explain`
  - `/quiz`
  - `/summarize`
  - `/learn/recommendations`

## 1. Install Python

Use Python 3.10 or newer.


Check:

```bash
python --version
```

## 2. Create a virtual environment

Windows:

```bash
python -m venv .venv
.venv\Scripts\activate
```

macOS/Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

## 3. Install dependencies

```bash
pip install -r requirements.txt
```

## 4. Configure Gemini

Copy `.env.example` to `.env`.

Windows:

```bash
copy .env.example .env
```

macOS/Linux:

```bash
cp .env.example .env
```

Then edit `.env`:

```env
GEMINI_API_KEY=your_real_api_key
GEMINI_MODEL=gemini-2.5-flash
LOCAL_EXPLANATION_MODEL=MBZUAI/LaMini-Flan-T5-783M
```

The original project document specifies Gemini 1.5 Pro. The model is configurable through `GEMINI_MODEL` so you can set an API-supported model without changing Python code.

## 5. Run the application

```bash
uvicorn main:app --reload
```

Open:

http://127.0.0.1:8000

API documentation:

http://127.0.0.1:8000/docs

## Project structure

```text
EduGenie/
├── main.py
├── explanation_module.py
├── qna.py
├── quiz_module.py
├── summary_module.py
├── learning_path.py
├── requirements.txt
├── .env.example
├── README.md
├── templates/
│   └── index.html
└── static/
    └── style.css
```

## Notes

The local LaMini-Flan-T5 model is downloaded by Hugging Face Transformers the first time the Explain feature is used. The download can be large.

Gemini-backed features require a valid API key and internet access.

Never commit `.env` or your API key to GitHub.
