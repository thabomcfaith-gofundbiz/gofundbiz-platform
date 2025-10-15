# gofundbiz-platform
AI-Enhanced Funding Platform | Technical Assessment
# AI-Enhanced Funding Platform

## Overview
An intelligent funding platform that uses AI/NLP to match campaigns with potential investors based on interests, investment history, and compatibility.

## Features
-  AI-powered investor matching using TF-IDF and cosine similarity
-  Smart scoring based on multiple factors (interests, funding range, past investments)
- Fraud risk detection using keyword analysis
- Clean React frontend with Tailwind CSS
- Fast FastAPI backend

## Tech Stack
**Backend:**
- FastAPI (Python 3.10+)
- Scikit-learn for NLP
- TF-IDF Vectorization
- Cosine Similarity

**Frontend:**
- React 18
- Tailwind CSS
- Fetch API

## AI/NLP Approach

### Matching Algorithm
1. **Text Vectorization**: Convert campaign and investor profiles to TF-IDF vectors
2. **Similarity Calculation**: Use cosine similarity to measure compatibility
3. **Score Boosting**: Adjust scores based on:
   - Funding range compatibility (+0.2)
   - Category match
   - Past investment relevance
4. **Ranking**: Sort by final score and return top 3

### Fraud Detection
Simple keyword-based detection checking for:
- High-risk terms (crypto, guaranteed returns, risk-free)
- Unrealistic funding goals (>R1M = medium risk)

### Scalability to Production

**Current Implementation:**
- In-memory investor data
- Simple TF-IDF matching
- Rule-based fraud detection

**Production Enhancements:**
- **Database**: PostgreSQL with vector extensions for similarity search
- **Advanced NLP**: 
  - Use sentence transformers (BERT, RoBERTa) for semantic matching
  - OpenAI embeddings API for better understanding
  - Fine-tuned models on funding domain data
- **ML Fraud Detection**:
  - Train on historical fraud patterns
  - Multi-factor risk scoring
  - Real-time anomaly detection
- **Caching**: Redis for frequently accessed investor profiles
- **Async Processing**: Celery for heavy ML computations
- **A/B Testing**: Track recommendation success rates

## Setup Instructions

### Prerequisites
- Python 3.10+
- Node.js 18+
- npm or yarn

### Backend Setup
```bash
cd backend
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn main:app --reload
