# Agentic Day 1 — LangChain Conversation History Demo

This repo contains a small Python script (`app.py`) that demonstrates the difference between:

- **Stateless** LLM calls (`llm.invoke("...")` called twice with no shared context)
- **Stateful / message-based** LLM calls (sending prior messages so follow-up questions like “this system” are grounded)

## Prerequisites

- **Conda** (recommended) — Miniconda or Anaconda
- **Python**: 3.10+ (3.11 recommended)
- **OpenAI API key** (required to run `ChatOpenAI`)

## Setup (Conda)

From the project root:

```bash
conda create -n agentic-day1 python=3.11 -y
conda activate agentic-day1
python -m pip install --upgrade pip
pip install -r requirements.txt
```

## Environment variables

This project loads environment variables from a local `.env` file via `python-dotenv`.

1. Create a `.env` file in the project root.
2. Add your API key:

```bash
OPENAI_API_KEY=your_openai_api_key_here
```

Notes:

- **Never commit** `.env` to version control.
- If you prefer, you can export variables in your shell instead of using `.env`.

## Run the app

```bash
python app.py
```

You should see three printed sections:

- **Response 1**: first stateless call
- **Response 2**: follow-up stateless call (may be ambiguous)
- **Response 3**: message-based call with conversation history (should be grounded)

## Troubleshooting

- **Authentication error / missing key**: confirm `OPENAI_API_KEY` is set (in `.env` or your shell).
- **Dependency issues**: re-run `pip install -r requirements.txt` inside the activated conda env.