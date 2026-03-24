# CalmSpace AI Agent

A compassionate, AI-powered mental health support chatbot that integrates with multiple channels including web and WhatsApp. SafeSpace provides evidence-based emotional support, therapeutic guidance, and connects users with professional help when needed.

## 🎯 Features

- **Intelligent Therapeutic Agent**: Powered by the MedGemma LLM with a warm, empathetic clinical psychology persona
- **Multi-Channel Support**:
  - Web interface via Streamlit
  - WhatsApp integration via Twilio
- **Smart Tool Integration**:
  - Mental health responses and guidance
  - Emergency contact system for crisis situations
  - Therapist finder for local professional help
- **LangGraph Workflow**: Advanced AI orchestration for complex multi-turn conversations
- **Multiple LLM Support**: Compatible with Groq, OpenAI, Ollama, and more

## 📋 Prerequisites

- Python 3.13 or higher
- Ollama (with MedGemma 4B model) or alternative LLM provider
- Streamlit (for web frontend)
- FastAPI & Uvicorn (backend server)
- Twilio account (for WhatsApp integration)

## 🚀 Installation

1. **Clone or extract the project** into your workspace

2. **Create and activate virtual environment**:

   ```powershell
   python -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```

3. **Install dependencies**:

   ```bash
   pip install -r requirements.txt
   ```

   Or using the project dependencies:

   ```bash
   pip install fastapi uvicorn streamlit langchain langgraph ollama python-multipart requests twilio pydantic
   ```

4. **Set up Ollama** (if using Ollama for LLM):

   ```bash
   ollama pull alibayram/medgemma:4b
   ```

5. **Configure environment variables** (create `.env` file if needed):
   - Twilio credentials for WhatsApp integration
   - LLM provider API keys (if not using Ollama)

### Backend Server (FastAPI)

```bash
python backend/main.py
```

The server will start at `http://localhost:8000`

**Available Endpoints**:

- `POST /ask` - Chat with the AI agent
  ```json
  {
    "message": "I'm feeling anxious"
  }
  ```
- `POST /whatsapp_ask` - WhatsApp message handler (Twilio webhook)

### Frontend (Streamlit)

```bash
streamlit run frontend.py
```

Opens at `http://localhost:8501`

## Core Components

### Agent (backend/agent.py)

- **Therapeutic Response Tool**: Generates empathetic, evidence-based mental health guidance
- **Emergency Call Tool**: Initiates emergency contact via Twilio for crisis situations
- **Therapist Finder**: Locates licensed mental health professionals nearby

### Backend (backend/main.py)

- FastAPI application handling HTTP requests
- Integrates with LangGraph for workflow orchestration
- Supports both REST API and WhatsApp (TwiML) responses

### Tools (backend/tools.py)

- **query_medgemma()**: Interfaces with MedGemma model through Ollama
- **call_emergency()**: Places emergency calls via Twilio
- **find_nearby_therapists_by_location()**: Searches for therapists using OpenStreetMap

## Usage Examples

### Via Web API

```bash
curl -X POST http://localhost:8000/ask \
  -H "Content-Type: application/json" \
  -d '{"message": "I am feeling overwhelmed"}'
```

### Via WhatsApp

Send a message to your Twilio-configured WhatsApp number, and SafeSpace will respond with therapeutic guidance.

## Safety & Emergency Features

SafeSpace is designed with safety as a priority:

- Detects keywords indicating suicidal ideation or self-harm
- Routes crisis situations to emergency contact system
- Provides warm handoffs to professional services
- Always encourages users to seek professional help when needed

## 📚 Dependencies Overview

| Package              | Purpose                      |
| -------------------- | ---------------------------- |
| fastapi, uvicorn     | Web server framework         |
| streamlit            | Web frontend interface       |
| langchain, langgraph | AI orchestration & workflows |
| ollama               | Local LLM inference          |
| twilio               | WhatsApp integration         |
| pydantic             | Data validation              |
| requests             | HTTP client for APIs         |

## 🔐 Configuration

Key configuration files:

- `backend/config.py` - Application settings
- `.env` - Environment variables (create as needed)
  - Twilio Account SID & Auth Token
  - Phone numbers for emergency services

## Testing

Test the tools with:

```bash
python backend/test_tool.py
```

## Contributing

Improvements welcome! Areas for enhancement:

- Adding more mental health tools
- Expanding LLM provider support
- Improving user interface
- Adding multi-language support

## Support & Resources

- **Mental Health Crisis**: Always seek immediate professional help or call emergency services
- **Professional Resources**: The app includes tools to find licensed therapists in your area
- **Twilio Docs**: https://www.twilio.com/docs/whatsapp
- **LangChain Docs**: https://python.langchain.com/

## ⚡ Important Notes

**Disclaimer**: SafeSpace is an AI assistant and not a replacement for professional mental health care. For emergencies or severe mental health concerns, please contact emergency services or a licensed mental health professional immediately.

---

Built with ❤️ for mental wellness
