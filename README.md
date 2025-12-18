# Aura Health: The Agentic Guardian

![Aura Health Banner](https://via.placeholder.com/560x280.png?text=Aura+Health+Dashboard)

> **Repository:** [github.com/bhaagavatham/AuraHealth](https://github.com/bhaagavatham/AuraHealth)  
> **Kaggle Notebook:** [Aura Health Solution](https://www.kaggle.com/code/bhaagavatham/aurahealth/)  
> **Competition Track:** AI for Good (Healthcare & Personal Safety)  
> **Stack:** Gemini 3.0 Pro (Reasoning), Gemini 2.5 Flash (Speed), Gemini Live (Native Audio/Video), Gemini 3 Pro Image (Vision).

---

## 🏆 Kaggle Competition Submission Materials

**Use the sections below to fill out your Kaggle Submission Form.**

### 1. Project Title & Description
**Title:** Aura Health: The First Agentic Guardian for Human Longevity  
**Subtitle:** A Multi-Agent Ecosystem for Coaching, Reasoning, and Emergency Response powered by Gemini 3.0.  

**Project Description:**
> **The Problem**  
> Current health apps are passive data silos. They record steps and sleep, but they don't *act*. They don't see you struggling with a workout, they don't reason why your energy is low, and critically, they cannot actively intervene during a medical emergency like a fall or cardiac event.
>
> **The Solution: Aura Health**  
> Aura Health is an "Agentic Companion"—a system that moves from passive tracking to active guardianship. Built on the Google Gemini 3.0 stack, Aura utilizes a multi-agent swarm to manage holistic well-being. It fits squarely into the **AI for Good** track by democratizing access to elite-level health coaching and emergency monitoring.
>
> **Key Innovations**  
> 1.  **Real-Time Multimodal Coaching (The Loop Agent):** Using the **Gemini Live API**, Aura acts as a personal trainer that can *see* via the camera. It processes video frames to correct posture and offer encouragement.  
> 2.  **Medical-Grade Reasoning (The Thinking Agent):** Aura employs **Gemini 3.0 Pro** with a `thinkingBudget`. It analyzes longitudinal data (Heart Rate + Sleep) to find complex correlations standard algorithms miss.  
> 3.  **Tiered Emergency Safety Net (The Guardian Agent):** The Safety Hub features a **Tiered SOS Protocol**. In the event of a fall, Aura sequentially contacts a Caregiver, Doctor, then EMS. It uses **Google Maps Grounding** to locate the nearest hospital and creates a "Live Video Uplink" for responders.  
> 4.  **Visual Motivation (The Vision Agent):** Leveraging **Gemini 3 Pro Image**, Aura visualizes the user's goals (e.g., "Running a marathon") to provide psychological priming.

---

### 2. Architecture & Design (Visual Architect)

**End-to-End Flow Diagram:**

```mermaid
graph TD
---
config:
  layout: fixed
---
flowchart TB
 subgraph subGraph0["Agent Swarm"]
        LiveAgent["<b>Coach Agent (Loop)</b><br>Gemini Live (Audio/Video)"]
        AnalystAgent["<b>Analyst Agent (Sequential)</b><br>Gemini 3.0 Pro (Thinking)"]
        GuardianAgent["<b>Guardian Agent (Parallel)</b><br>Gemini 2.5 Flash + Tools"]
        VisionAgent["<b>Vision Agent</b><br>Gemini 3 Pro Image"]
  end
 subgraph subGraph1["Safety & Tools"]
        Haptic["Nudge Engine™<br>(Vibration API)"]
        Geo["Geolocation API"]
  end
 subgraph subGraph2["Aura Health App (Client)"]
        Orchestrator["<b>Orchestrator</b><br>Router &amp; State Manager"]
        subGraph0
        subGraph1
  end
 subgraph subGraph3["External World"]
        MapsAPI["Google Maps Platform"]
        Responders["Emergency Contacts / 911"]
  end
    User(("User")) <-- "Real-time A/V" --> LiveAgent
    User -- Biometrics --> Orchestrator
    Orchestrator -- Batch JSON --> AnalystAgent
    Orchestrator -- SOS Trigger --> GuardianAgent
    Orchestrator -- Goal Text --> VisionAgent
    GuardianAgent -- Locate --> MapsAPI
    GuardianAgent -- Call/Alert --> Responders
    GuardianAgent -- Haptic Feedback --> Haptic
    LiveAgent -. Visual Feedback .-> User
    AnalystAgent -. Insights .-> User
```
---

### 3. Key Concepts Implemented

This project demonstrates mastery of the "5-Day Agents" curriculum:

1.  **Multi-Agent System (Parallel & Sequential):**
    *   *Analyst:* Sequential agent processing data -> reasoning -> output.
    *   *Coach:* Loop agent handling continuous WebSocket streams.
    *   *Guardian:* Parallel agent monitoring sensors while executing countdown logic.
2.  **Tools & Grounding:**
    *   **Google Maps:** Used in `findEmergencyServices` to ground the agent in physical reality.
    *   **Native Sensors:** Microphone, Camera, and Vibration (Nudge Engine) used as input/output tools.
3.  **Observability & Trust:**
    *   **Safety Hub:** Logs every automated action (e.g., "Dialing 911", "Location Sent").
    *   **Social Hub:** A "Life Stream" dashboard showing agent autonomy.

---

### 4. Sample Datasets (for Production/Testing)

Upload these as JSON/CSV files to Kaggle to fulfill the data requirement.

**A. `patient_biometrics.json`**
```json
[
  {
    "user_id": "u_001",
    "timestamp": "2024-03-10T08:00:00Z",
    "heart_rate_avg": 72,
    "sleep_quality_score": 85,
    "steps": 10240,
    "fall_risk_index": 12
  },
  {
    "user_id": "u_001",
    "timestamp": "2024-03-11T08:00:00Z",
    "heart_rate_avg": 68,
    "sleep_quality_score": 92,
    "steps": 11500,
    "fall_risk_index": 10
  }
]
```

**B. `emergency_contacts_schema.csv`**
```csv
contact_id,role,priority_level,notification_method,response_timeout_sec
c_01,PRIMARY_CAREGIVER,1,VOICE_CALL,180
c_02,DOCTOR_SPECIALIST,2,SMS_ALERT,300
c_03,EMS_DISPATCH,3,GPS_DATA_LINK,0
```

---

## 🛠️ Installation & Setup

1.  **Clone:** `git clone https://github.com/bhaagavatham/AuraHealth`
2.  **Install:** `npm install`
3.  **Run:** `npm start`
4.  **Auth:** The app handles API Key selection via the AI Studio overlay.
