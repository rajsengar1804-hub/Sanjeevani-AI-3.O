# 🌿 Sanjeevani AI
### AI That Cares. A Safer Tomorrow.

**Sanjeevani AI** is an intelligent safety-monitoring system designed to help protect elderly people and other vulnerable individuals. It combines computer vision, pose estimation, spatial monitoring, and distress detection concepts to identify potential emergencies and support timely caregiver responses.

🌐 **Live Deployment:** [Sanjeevani AI](https://sanjeevani-ai-beta.vercel.app/)

---
## License

This project is licensed under the MIT License. See the [LICENSE.txt](LICENSE.txt) file for details.


## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Key Features](#-key-features)
- [Technology Stack](#-technology-stack)
- [System Workflow](#-system-workflow)
- [Project Structure](#-project-structure)
- [Prerequisites](#-prerequisites)
- [Installation and Setup](#-installation-and-setup)
- [Environment Variables](#-environment-variables)
- [Running the Application](#-running-the-application)
- [Deployment](#-deployment)
- [Privacy and Security](#-privacy-and-security)
- [Testing](#-testing)
- [Limitations](#-limitations)
- [Future Enhancements](#-future-enhancements)
- [License](#-license)

## 🎯 Project Overview

Elderly individuals may experience falls, abnormal vital signs, or other emergencies when immediate assistance is unavailable. Sanjeevani AI aims to address this problem through intelligent monitoring and a progressive emergency-response workflow.

The proposed system combines real-time movement analysis, bed-zone monitoring, wearable vital-sign integration, and voice-based distress detection.

When a potential emergency is identified, the system can initiate a sequence of checks and alerts intended to notify a caregiver and support further escalation.

The project emphasizes three main goals:

- **Safety:** Identify potential emergencies as early as possible.
- **Privacy:** Perform video analysis locally when supported by the edge-processing implementation.
- **Reliability:** Reduce false alarms through temporal reasoning and confirmation mechanisms.

> **Important:** The deployed dashboard and the complete real-time monitoring system may have different implementation status. Actual camera inference, wearable integration, caregiver notifications, and emergency-service dispatch must be verified against the source code and deployment configuration.

## 🚀 Key Features

### 1. Real-Time Fall Detection
Uses human pose estimation and movement analysis to identify posture changes and potential falls.

### 2. Intelligent Bed-Zone Monitoring
Uses a calibrated spatial region to distinguish ordinary bed-related movements from potentially dangerous movement patterns.

### 3. Wearable Vital-Sign Monitoring
Designed to integrate readings such as heart rate and identify unusual values that may require attention.

### 4. Voice-Based Distress Detection
Supports a proposed voice-command workflow in which a distress phrase, such as "Sanjeevani, I need help," can initiate an assistance request.

### 5. Progressive Emergency Escalation
The intended response workflow includes:

- **Level 1 — Verification:** Ask whether the person is okay.
- **Level 2 — Caregiver Alert:** Notify a designated caregiver if the concern remains unresolved.
- **Level 3 — Further Escalation:** Support escalation to emergency services when configured and appropriately authorized.

### 6. Monitoring Dashboard
The web interface is built to present safety-related information and monitoring status through an interactive dashboard.

## 🛠️ Technology Stack

| Component | Technology |
|---|---|
| Frontend framework | React |
| Build tool | Vite |
| Styling | Tailwind CSS |
| Animations | Framer Motion |
| Client-side routing | React Router |
| Object detection | YOLOv8 |
| Pose estimation | MediaPipe Pose |
| Computer vision | OpenCV |
| Backend and inference logic | Python |
| Deployment platform | Vercel for the web application |

The actual dependencies and versions should be confirmed using the project's package files and Python dependency list.

## 🧠 System Workflow

The intended monitoring pipeline follows these stages:

1. **Video Input:** Receive frames from a supported camera or video source.
2. **Person Detection:** Use YOLOv8 to detect and track a person.
3. **Pose Estimation:** Use MediaPipe Pose to extract body landmarks.
4. **Movement Analysis:** Examine posture, joint angles, vertical displacement, and movement over time.
5. **Context Evaluation:** Consider bed-zone position and recovery movement to distinguish ordinary activity from a possible fall.
6. **Distress Verification:** Process a supported voice command or ask the user for confirmation.
7. **Alert Dispatch:** Trigger the configured caregiver notification or escalation workflow.

### Architecture Overview

```text
       Camera / Video Input
                |
                v
       Person Detection
           (YOLOv8)
                |
                v
       Pose Estimation
       (MediaPipe Pose)
                |
                v
       Temporal Analysis
                |
                v
      Context & Risk Check
       /              \
      v                v
Normal Activity    Possible Emergency
                       |
                       v
               Voice Verification
                       |
                       v
               Caregiver Alert
                       |
                       v
             Further Escalation
```

This diagram represents the intended system architecture. The availability of each stage depends on the implemented modules and runtime configuration.

## 📁 Project Structure

The following is a suggested structure. Adapt the directory names to match the actual repository.

```text
sanjeevani-ai/
├── public/
├── src/
│   ├── components/
│   ├── pages/
│   ├── assets/
│   ├── App.jsx
│   └── main.jsx
├── backend/
│   ├── app.py
│   ├── requirements.txt
│   └── ...
├── tests/
├── .env.example
├── .gitignore
├── index.html
├── package.json
├── README.md
├── TECHNICAL_DESIGN.md
└── LICENSE
```

The Python backend and test directories should only be listed as existing components once they are present in the repository.

## 💻 Prerequisites

Install the following tools before starting development:

- Node.js and npm
- Git
- A code editor such as Visual Studio Code
- Python 3.x if running the Python backend
- A compatible camera or video source for real-time inference

Confirm your installations:

```bash
node --version
npm --version
git --version
python --version
```

Depending on your operating system, you may need to use `python3 --version` instead.

## ⚙️ Installation and Setup

### Step 1: Clone the Repository

Replace the example repository URL with the actual GitHub repository URL.

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd sanjeevani-ai
```

### Step 2: Install Frontend Dependencies

```bash
npm install
```

### Step 3: Configure Environment Variables

Create a `.env` file in the project root if the application requires environment variables.

For a Vite frontend that communicates with a backend, an example configuration is:

```env
VITE_API_BASE_URL=http://localhost:8000
```

This variable is an example, not a confirmed requirement of the current deployment.

### Step 4: Set Up the Python Backend

If the repository contains a Python backend with a `requirements.txt` file, create and activate a virtual environment.

```bash
python -m venv .venv
```

On Windows:

```bash
.venv\Scripts\activate
```

On macOS or Linux:

```bash
source .venv/bin/activate
```

Install the dependencies:

```bash
pip install -r backend/requirements.txt
```

The command assumes the dependency file is located at `backend/requirements.txt`. Adjust the path to match the repository.

### Step 5: Download Required ML Models

If real-time inference is implemented, obtain the required YOLOv8 weights and configure MediaPipe Pose according to the backend implementation.

Follow the applicable model licenses and verify model paths before starting inference.

## 🔐 Environment Variables

Environment variables allow configuration to be separated from application code.

| Variable | Example | Purpose |
|---|---|---|
| `VITE_API_BASE_URL` | `http://localhost:8000` | Backend API base URL, if used by the frontend |
| `PORT` | `8000` | Backend listening port, if supported |
| `MODEL_PATH` | `models/best.pt` | Optional path to a trained YOLO model |
| `ALERT_API_KEY` | Not provided | Optional secret for an external alert service |

Only configure variables that the application actually reads. The names above are illustrative and may need to be changed to match the implementation.

**Security guidelines:**

- Never commit real API keys, passwords, or tokens.
- Add `.env` files to `.gitignore`.
- For Vercel deployments, configure required variables in the project's environment-variable settings.
- Vite exposes variables prefixed with `VITE_` to client-side code. Never put secrets in them.
- Keep private credentials and notification-service keys on the backend.

## ▶️ Running the Application

### Start the Frontend

From the directory containing `package.json`, run:

```bash
npm run dev
```

Vite normally prints a local development URL, often:

```text
http://localhost:5173
```

Open the URL shown in your terminal.

### Start the Python Backend

If a Python API is implemented using a compatible application framework, start it using the repository's documented entry point.

For example, if the backend uses FastAPI and defines an `app` object in `backend/app.py`:

```bash
uvicorn app:app --app-dir backend --reload --port 8000
```

This command is applicable only if the project uses FastAPI and the stated entry point exists.

### Build for Production

```bash
npm run build
```

To preview the production build locally:

```bash
npm run preview
```

## 🌐 Deployment

The Sanjeevani AI web application is available at:

**[https://sanjeevani-ai-beta.vercel.app/](https://sanjeevani-ai-beta.vercel.app/)**

For a Vercel deployment:

1. Push the project to a GitHub repository.
2. Import the repository into Vercel.
3. Configure the frontend build command and output directory according to the Vite project configuration.
4. Add any required environment variables.
5. Deploy the application and verify the resulting URL.

A Vercel-hosted frontend does not automatically host a continuously running Python computer-vision process. If real-time inference requires a separate service, deploy the backend or edge-processing component to a compatible environment and configure the frontend API URL.

## 🔒 Privacy and Security

Sanjeevani AI is designed with privacy-conscious monitoring in mind.

- Process video locally when supported by the edge implementation.
- Avoid uploading raw video unless required, disclosed, and authorized.
- Protect caregiver contact information and wearable data.
- Secure APIs and credentials.
- Limit access to monitoring information.
- Provide appropriate consent and data-retention controls.

Privacy claims should reflect the actual data flow of the deployed system, including any external APIs or cloud services.

## 🧪 Testing

Testing should cover both normal activity and potential emergency scenarios.

| Test Case | Input or Scenario | Expected Result |
|---|---|---|
| TC-01 | Person standing or walking normally | No fall alert |
| TC-02 | Simulated fall movement | Potential fall detected |
| TC-03 | Person lies down intentionally in the bed zone | Bed-related activity is handled appropriately |
| TC-04 | Person leaves the configured bed zone | Zone transition is identified |
| TC-05 | Recognized distress command | Assistance workflow starts |
| TC-06 | No response to a verification prompt | Configured escalation policy is followed |
| TC-07 | Missing or unavailable camera input | Clear error or unavailable status |
| TC-08 | Missing backend configuration | Clear configuration error |

These are proposed test cases, not claims that the current application has passed them. Use controlled test data and simulated emergencies; do not rely on the application as the sole means of emergency protection.

## ⚠️ Limitations

- Detection accuracy depends on lighting, camera placement, occlusion, model quality, and movement patterns.
- A web dashboard alone does not guarantee real-time inference.
- Wearable monitoring requires compatible data sources and integration.
- Voice detection depends on microphone access and supported speech-processing components.
- Caregiver alerts and emergency-service escalation require working integrations, network connectivity, and appropriate authorization.
- Automated detection can produce false positives and false negatives.

Sanjeevani AI is a safety-support project and should not be treated as a replacement for professional medical care or a verified emergency-response service.

## 🔮 Future Enhancements

- Integrate live camera feeds with edge-based inference.
- Improve fall detection using temporal movement analysis.
- Connect supported wearable devices for vital-sign monitoring.
- Add authenticated caregiver accounts and alert history.
- Implement secure, reliable notification delivery.
- Add configurable monitoring zones and accessibility options.
- Evaluate detection accuracy using documented datasets and controlled tests.
- Add automated unit, integration, and end-to-end testing.

## 📄 License

This project is distributed under the license specified in the repository's `LICENSE` file.

If the project uses the MIT License, include the complete MIT license text and the appropriate copyright holder and year. Do not describe the project as MIT-licensed until that license has been selected and added.

---

**Sanjeevani AI — AI that cares. A safer tomorrow.**
