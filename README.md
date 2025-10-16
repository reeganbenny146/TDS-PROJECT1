# TDS PROJECT: Gemini Automated Task Receiver & AI Code Deployment

This project is part of the **Tools for Data Science (TDS) course**. It provides a FastAPI-based service that automates receiving coding tasks, generating code using Google Gemini LLM, saving files, deploying to GitHub, and enabling GitHub Pages for live previews.

---

## Features

- **Receives tasks** via a `/ready` endpoint (with instructions, checks, and attachments)
- **Verifies security** using a student secret
- **Generates code** and project files using Gemini LLM (Google API)
- **Saves files and attachments** locally
- **Creates or updates GitHub repositories** and pushes generated code
- **Enables GitHub Pages** for live web previews
- **Notifies an evaluation server** with deployment details

---

## Project Structure

- `main.py` &mdash; FastAPI app and orchestration logic
- `models.py` &mdash; Pydantic models for task requests
- `config.py` &mdash; Environment variable management
- `requirements.txt` &mdash; Python dependencies
- `Dockerfile` &mdash; Containerization for deployment
- `.env` &mdash; API keys and secrets (do not share publicly!)

---

## Setup & Usage

### 1. Clone the repository

```bash
git clone https://github.com/reeganbenny/TDS-PROJECT1.git
cd TDS-PROJECT1
```

### 2. Create and activate a virtual environment

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure environment variables

Edit the `.env` file with your own API keys, GitHub token, and username.

### 5. Run the FastAPI app

```bash
uvicorn main:app --host 0.0.0.0 --port 7860
```

Or, using Docker:

```bash
docker build -t gemini_project .
docker run -p 7860:7860 gemini_project
```

---

## API Endpoints

- `POST /ready` &mdash; Receive and process a new coding task
- `GET /` &mdash; Health check
- `GET /status` &mdash; Service status

---

## Environment Variables (`.env`)

- `GEMINI_API_KEY` &mdash; Google Gemini API key
- `GITHUB_TOKEN` &mdash; GitHub personal access token (with repo permissions)
- `GITHUB_USERNAME` &mdash; Your GitHub username
- `STUDENT_SECRET` &mdash; Secret for authenticating incoming tasks

---

## Security

- Never share your `.env` file or API keys publicly.
- Use a GitHub token with the minimum required permissions.

---

## License

MIT License

---

## Author

[reeganbenny](https://github.com/reeganbenny)
