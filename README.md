# Offline Interview Recorder with Whisper AI

A local client–server web application that records interview answers and automatically converts recorded videos into text and AI-generated feedback using Whisper.

---

## Overview

This project allows users to record interview answers one question at a time (up to 5 questions).  
Each recorded answer is uploaded immediately to the backend, where it is processed by an offline AI pipeline to generate a transcript and a short summary or feedback.

The system is designed for **local execution**, making it suitable for coursework, demonstrations, and privacy-sensitive use cases.

---

## Key Features

- Record interview answers sequentially (Q1 → Q5)
- One video file per question
- Upload is required before moving to the next question
- Automatic stop after a time limit (default: 60 seconds)
- Offline speech-to-text using Whisper
- AI-generated transcript and feedback for each answer
- Results are stored and displayed per question
- Client-server architecture with clear separation of concerns

---

## AI Processing Workflow

1. The frontend records video and audio using the browser MediaRecorder API.
2. The recorded video is uploaded to the backend server.
3. FFmpeg extracts and converts audio from video into WAV format.
4. Whisper runs locally to transcribe speech into text.
5. A lightweight AI summarization step generates feedback.
6. The transcript and summary are returned to the frontend and saved per question.

---

## Technology Stack

### Frontend
- React
- Vite
- JavaScript
- MediaRecorder API

### Backend
- Node.js
- Express
- FFmpeg
- Whisper (local, offline)
- Python (AI processing scripts)

---

## Project Structure

Offline_interview_recorder_whisper/
├── backend/
│ ├── index.js
│ ├── run_whisper_local.js
│ ├── whisper_local.py
│ ├── ai_summary.py
│ └── storage/
├── frontend/
│ ├── src/
│ │ ├── App.jsx
│ │ └── App.css
│ └── vite.config.js
└── README.md


---

## How to Run Locally

### Backend Setup

'''bash
cd backend
npm install
npm run dev
Backend server runs at:
http://localhost:4000

Frontend Setup
bash
cd frontend
npm install
npm run dev
Open in browser:
http://localhost:5173

API Flow (Simplified)
1. Verify token
2. Start session
3. Upload recorded video (per question)
4. AI processing (Whisper + summarization)
5. Finish session

## Security and Constraints
- Token verification is handled on the server
- Upload order is enforced (cannot skip questions)
- File size and MIME type are validated
- Designed for local or internal use (not public deployment)

## Use Case and Purpose
This project demonstrates:
- Client-server communication
- Media recording in web browsers
- Offline AI integration
- Practical usage of FFmpeg and Whisper
- Full-stack development with React and Node.js
It is suitable for academic projects and personal portfolio presentations.



