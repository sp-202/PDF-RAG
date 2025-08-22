# Local RAG Pipeline with Ollama LLaMA

This repository implements a **local Retrieval-Augmented Generation (RAG) pipeline** using Chroma embeddings and Ollama LLaMA models, designed to run efficiently on an RTX 4060 GPU. It supports semantic search, LLM querying, and LangChain tracing, allowing you to build a fast, local, AI-powered question-answering system over large documents.

---

## Features

- Split large PDF documents into chunks for better retrieval
- Embed chunks locally using **e5-base-v2**
- Store embeddings in **Chroma** vectorstore
- Perform **semantic search** with cosine similarity
- Query **LLaMA or any models** running in Docker via Ollama API
- Track LLM calls with **Langsmith tracing**
- Safe configuration using `.env` for API keys
- Lightweight and GPU-friendly models (`gemma2:2b`) and higher-quality options (`llama3.1`)

---

## Requirements

- Python 3.10+
- Docker + Docker Compose
- RTX 4060 GPU with 8GB VRAM (recommended)
- Optional: Langsmith account for tracing

---

## Setup

1. **Clone the repository**

```bash
git clone https://github.com/sp-202/PDF-RAG.git
cd PDF-RAG
uv venv .venv
source .venv/bin/activate  # Linux/macOS
.venv\Scripts\activate     # Windows
uv install
```

2. **Docker Ollama Setup**
```bash
sudo docker compose -d

# List available models
sudo docker exec -it ollama ollama list

# Use gemma2:2b for 8GB GPU-friendly queries
# Use llama3.1 for larger, more complex reasoning

# Pull new model if needed
sudo docker exec -it ollama ollama pull gemma2:2b
sudo docker exec -it ollama ollama pull llama3.1
```
2. **Add .env file**
```
# .env
LANGCHAIN_TRACING_V2="true"
LANGCHAIN_ENDPOINT="https://api.smith.langchain.com"
LANGCHAIN_API_KEY="<your-api-key>"
LANGSMITH_PROJECT="<your-project-id>"
```

