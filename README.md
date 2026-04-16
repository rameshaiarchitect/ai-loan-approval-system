# AI Loan Approval System

Event-driven microservices system for loan processing and credit
evaluation.

This project demonstrates a real-world architecture using Java, Python,
Kafka, and Docker.

------------------------------------------------------------------------

## 🧠 Overview

The system processes loan applications asynchronously:

1.  User submits loan request via REST API
2.  Loan Service publishes event to Kafka
3.  Credit Agent consumes event and evaluates risk
4.  Decision is generated (APPROVED / REJECTED)

------------------------------------------------------------------------

## 🏗️ Architecture

Client ↓ Loan Service (Spring Boot) ↓ Kafka (Event Streaming) ↓ Credit
Agent (FastAPI) ↓ Decision Output

------------------------------------------------------------------------

## 🔗 Repositories

### Loan Service (Java - Spring Boot)

Handles API requests and publishes Kafka events.

https://github.com/rameshaiarchitect/ai-loan-loan-service

------------------------------------------------------------------------

### Credit Agent (Python - FastAPI)

Consumes events and evaluates credit decisions.

https://github.com/rameshaiarchitect/ai-loan-credit-agent

------------------------------------------------------------------------

### Infrastructure (Docker)

Provides Kafka, Zookeeper, Postgres, Redis.

https://github.com/rameshaiarchitect/ai-loan-infra

------------------------------------------------------------------------

## ⚙️ Tech Stack

-   Java (Spring Boot)
-   Python (FastAPI)
-   Apache Kafka
-   Docker & Docker Compose
-   Postgres
-   Redis

------------------------------------------------------------------------

## 🔄 Event Flow

POST /loan/apply ↓ Loan Service ↓ Kafka Topic:
loan.application.submitted ↓ Credit Agent ↓ Decision (APPROVED /
REJECTED)

------------------------------------------------------------------------

## ▶️ How to Run (Local Setup)

### 1. Start Infrastructure

git clone https://github.com/rameshaiarchitect/ai-loan-infra\
cd ai-loan-infra\
docker compose up -d

------------------------------------------------------------------------

### 2. Start Loan Service

git clone https://github.com/rameshaiarchitect/ai-loan-loan-service\
cd ai-loan-loan-service\
mvn spring-boot:run

------------------------------------------------------------------------

### 3. Start Credit Agent

git clone https://github.com/rameshaiarchitect/ai-loan-credit-agent\
cd ai-loan-credit-agent\
uv run uvicorn app.main:app --reload

------------------------------------------------------------------------

### 4. Test the System

curl -X POST http://localhost:8080/loan/apply\
-H "Content-Type: application/json"\
-d '{ "applicationId": "TEST123", "amount": 10000, "salary": 5000 }'

------------------------------------------------------------------------

## 🧪 Testing

### Loan Service

-   Unit Tests
-   Integration Tests using Testcontainers (Kafka)
-   JaCoCo coverage

------------------------------------------------------------------------

### Credit Agent

-   Unit Tests (decision logic, consumer logic, API)
-   Pytest with coverage (\~80%+)

------------------------------------------------------------------------

## 📊 Key Highlights

-   Event-driven architecture using Kafka
-   Polyglot microservices (Java + Python)
-   Real Kafka integration (not mocked)
-   Testcontainers for reliable integration testing
-   Docker-based local environment
-   Clean separation of concerns

------------------------------------------------------------------------

## 🚀 Future Improvements

-   Switch to JSON-based event payload
-   Implement real credit scoring logic
-   Publish decision to Kafka (new topic)
-   Persist data in Postgres
-   Add retry and DLQ handling
-   Introduce CI/CD pipeline

------------------------------------------------------------------------

## 👤 Author

Ramesh Kolamala\
GitHub: https://github.com/rameshaiarchitect
