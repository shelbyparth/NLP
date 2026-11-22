# VeriFact AI – AI-Powered Article Fact-Checking & Evidence Verification

VeriFact AI is an NLP-based fact-checking platform designed to analyze textual claims, retrieve relevant evidence, and evaluate whether claims are supported, contradicted, or lack sufficient evidence.

The platform combines Natural Language Processing (NLP), Natural Language Inference (NLI), hybrid information retrieval, and Large Language Models (LLMs) to provide evidence-based explanations and make fact verification more accessible.

## 🚀 Key Features

- **Article Verification:** Analyze submitted text and identify claims that require verification.
- **Evidence Retrieval:** Retrieve relevant passages from the local evidence corpus using hybrid search.
- **NLI-Based Stance Classification:** Classify evidence as supporting, contradicting, neutral, or unassessed.
- **AI-Generated Explanations:** Generate readable explanations using Google's Gemini API.
- **Article Summarization:** Generate short and detailed summaries of articles.
- **Claim and Entity Extraction:** Identify important claims and entities from submitted content.
- **Personalized News:** Discover news articles based on topics of interest.
- **Ask AI About Evidence:** Ask questions and receive answers grounded in available evidence.
- **Verification History:** Store and review previous verification results using SQLite.
- **Evidence Management:** Maintain a local evidence collection for retrieval and verification.

## 🛠️ Technology Stack

| Component | Technologies |
|---|---|
| Frontend | React, TypeScript, Vite |
| Backend | Python, FastAPI |
| NLP | Natural Language Processing |
| NLI | DeBERTa-based NLI model |
| Semantic Retrieval | Sentence Transformers, MiniLM |
| Text Retrieval | TF-IDF, Cosine Similarity |
| AI Explanation | Google Gemini API |
| News Search | Tavily API |
| Database | SQLite |
| Development Tools | VS Code, Git, GitHub |

## 🏗️ System Architecture

VeriFact AI follows a frontend-backend architecture.

1. **User Input:** The user submits an article, text, claim, or question through the React interface.
2. **Text Preprocessing:** The backend normalizes and prepares the submitted text.
3. **Claim Extraction:** Important claims are extracted from the content.
4. **Evidence Retrieval:** Relevant passages are retrieved from the local evidence corpus using hybrid semantic and TF-IDF retrieval.
5. **Stance Classification:** The NLI model evaluates the relationship between each claim and its retrieved evidence.
6. **Verdict Generation:** The system aggregates the evidence classifications to determine the verification assessment.
7. **AI Explanation:** Gemini generates a natural-language explanation using the retrieved evidence.
8. **Result Display:** The frontend displays the verdict, evidence matches, explanation, and relevant details.

## 📂 Project Structure

```text
verifact-ai/
│
├── backend/
│   ├── app/
│   │   ├── main.py
│   │   ├── config.py
│   │   ├── api/
│   │   ├── services/
│   │   │   ├── retrieval.py
│   │   │   ├── stance_classification.py
│   │   │   ├── verification.py
│   │   │   ├── rag_engine.py
│   │   │   └── corpus.py
│   │   └── ...
│   │
│   ├── data/
│   ├── requirements.txt
│   ├── .env.example
│   └── .env
│
├── frontend/
│   ├── src/
│   │   ├── App.tsx
│   │   └── ...
│   ├── package.json
│   └── ...
│
└── README.md
```

*The structure above highlights the main project components; additional files and folders may exist in your implementation.*

## ⚙️ Installation and Setup

### Prerequisites

- Python and pip
- Node.js and npm
- Git
- Visual Studio Code (recommended)

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/verifact-ai.git
```

Navigate to the project directory:

```bash
cd verifact-ai
```

### 2. Backend Setup

Open a terminal and navigate to the backend:

```bash
cd backend
```

Create a virtual environment:

```bash
python -m venv .venv
```

Activate the environment on Windows Git Bash:

```bash
source .venv/Scripts/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

### 3. Configure Environment Variables

Create a `.env` file inside the `backend` directory.

Add the API keys and configuration values required by your backend. For example:

```env
VERIFACT_GEMINI_MODEL=gemini-3.5-flash-lite
VERIFACT_USE_SEMANTIC=1
```

Configure your Gemini API key, Tavily API key, and local NLI model path using the exact variable names expected by `backend/app/config.py`.

**Important:** Never upload your `.env` file or expose API keys on GitHub.

### 4. Start the Backend

From the `backend` directory, activate the virtual environment and run:

```bash
uvicorn app.main:app --reload --port 8000
```

Backend address:

```text
http://localhost:8000
```

### 5. Frontend Setup

Open a second terminal:

```bash
cd frontend
```

Install frontend dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Open the frontend in your browser:

```text
http://localhost:5173/
```

Keep both frontend and backend terminals running while using the application.

## 🧠 Verification Methodology

VeriFact AI uses a combination of retrieval and inference techniques.

**1. Hybrid Evidence Retrieval**

The retrieval system combines:
- Semantic similarity using Sentence Transformers.
- Word-level TF-IDF similarity.
- Character-level TF-IDF similarity.
- Cosine similarity for relevance scoring.

**2. Natural Language Inference**

The NLI model compares claims against retrieved evidence and classifies the relationship between them.

**3. Evidence-Based Assessment**

The system produces the following assessment categories:

| Assessment | Meaning |
|---|---|
| Supported | Retrieved evidence supports the claim. |
| Contradicted | Retrieved evidence contradicts the claim. |
| Insufficient Evidence | Available evidence is not sufficient to establish a reliable assessment. |

Uncertain evidence is kept unclassified rather than being forced into a supporting or contradicting category.

## 🔐 Privacy and Security

- API keys are stored in environment variables.
- Local evidence and verification history are maintained by the backend.
- The NLI model can be loaded from a local model directory.
- API credentials should never be committed to a public repository.
- Avoid uploading private or confidential documents to a public evidence corpus.

## ⚠️ Limitations

- Verification quality depends on the relevance and reliability of available evidence.
- Claims outside the available evidence corpus may receive an insufficient-evidence assessment.
- AI-generated explanations may occasionally be unavailable due to API service interruptions.
- NLI models can produce uncertain classifications for ambiguous or context-dependent statements.
- This project is an experimental fact-checking aid and should not replace professional verification or authoritative sources.

## 🔮 Future Enhancements

- Expand the evidence corpus with trusted sources.
- Improve claim extraction and entity recognition.
- Add more advanced evidence ranking and source reliability assessment.
- Improve multilingual claim verification.
- Enhance verification performance and response time.
- Add richer visual analytics and evidence relationship views.
- Improve user authentication and personalized verification history.

## 👨‍💻 Development

This project is developed using a modular architecture, separating the frontend, backend, evidence retrieval, stance classification, and explanation generation components.

Contributions, suggestions, and improvements are welcome.

## 📄 License

This project is intended for educational and research purposes. Add an appropriate open-source license before distributing it publicly.

---

**VeriFact AI – Making Information Verification Smarter Through AI and Evidence.**
