# 🔒 Permission Analyzer

A privacy-first Chrome extension that monitors real-time browser permission usage. Track exactly when websites access your camera, microphone, location, and more — even with pre-granted permissions.

![Chrome Extension](https://img.shields.io/badge/Chrome-Extension-4285F4?style=flat-square&logo=googlechrome&logoColor=white)
![Manifest V3](https://img.shields.io/badge/Manifest-V3-orange?style=flat-square)
![Privacy First](https://img.shields.io/badge/Privacy-First-00C853?style=flat-square)

---

## 🎯 Overview

Modern browsers silently grant permissions once you click "Allow". Websites can then access your camera, microphone, or location **anytime** without asking again. Users have no visibility into:

- When permissions are actually being used
- Which websites are accessing what  
- How often their data is being accessed

**Permission Analyzer** provides real-time monitoring and comprehensive logging of all permission usage, giving you complete transparency and control.

---

## ✨ Key Features

### 🔍 Real-Time Active Monitoring
Detects **active permission usage** — not just when you grant permissions, but every time a website actually uses them.

**Tracked Permissions:**

| Permission | Description |
|------------|-------------|
| 📷 Camera | Video stream access for video calls and recording |
| 🎤 Microphone | Audio stream access for voice chat and recording |
| 📍 Location | GPS and geolocation API calls |
| 📋 Clipboard | Clipboard read operations |
| 🔔 Notifications | Push notification requests |

### 🛡️ Privacy-Focused Architecture
- ✅ No external servers — all data stays on your device
- ✅ No analytics or tracking — zero telemetry
- ✅ Local storage only using `chrome.storage.local`
- ✅ Open source with fully auditable code

### 📊 Comprehensive Dashboard
- View all logged permission accesses with precise timestamps
- Filter by permission type or domain
- Export logs as Markdown for auditing
- Real-time statistics and usage insights

### ⚡ Performance Optimized
- Lightweight footprint under 100KB
- Minimal CPU and memory usage
- Background service worker sleeps when idle
- Smart deduplication prevents log spam

---

## 🚀 Installation

### From Source

**1. Clone the repository**
```bash
git clone https://github.com/yourusername/permission-analyzer.git
cd permission-analyzer
```

**2. Load in Chrome**
- Open `chrome://extensions/`
- Enable "Developer mode" in the top right
- Click "Load unpacked"
- Select the project folder

**3. Start monitoring**
- Extension icon appears in your toolbar
- Visit any website and the extension automatically monitors
- Click the icon to view detailed logs

---

## 🔧 Technical Architecture

### System Flow
```
Website uses permission (e.g., camera)
         ↓
API Interceptor catches the call
         ↓
Content Script sends to Background Worker
         ↓
Stored in chrome.storage.local
         ↓
UI updates in real-time
```

### 🛠️ Core Technologies

| Category | Technology |
|----------|------------|
| **Platform** | Chrome Extension (Manifest V3) |
| **Languages** | JavaScript (ES6+), HTML5, CSS3 |
| **Styling** | Tailwind CSS |
| **Storage** | chrome.storage.local API |
| **APIs** | Chrome Extensions API, Web APIs |

### 💡 Detection Methodology

Unlike basic permission trackers, Permission Analyzer uses **API interception** to detect actual usage:

```javascript
const original = navigator.mediaDevices.getUserMedia;
navigator.mediaDevices.getUserMedia = function(constraints) {
  logPermissionUsage('camera', window.location.href);
  return original.apply(this, arguments);
};
```

This approach ensures **100% accuracy** — every time a website accesses a permission, it is logged, regardless of pre-granted settings.

---

## 🎓 Use Cases

### For Privacy-Conscious Users
- Track which websites access your camera and microphone
- Identify privacy-invasive websites and patterns
- Audit permission usage over time for security awareness

### For Security Professionals
- Monitor corporate communication tools (Zoom, Teams, Slack)
- Export logs for transparency and compliance reports
- Identify unexpected or unauthorized permission access

### For Developers
- Debug permission-related issues in web applications
- Test permission flows and user experiences
- Study Chrome extension development and API patterns

---

## 🔐 Security & Privacy

### Data Collection Policy
- 🚫 Zero data leaves your browser
- 🚫 No external API calls
- 🚫 No third-party services
- 🚫 No user tracking or analytics

### Required Permissions

| Permission | Purpose |
|------------|---------|
| `storage` | Save logs locally on device |
| `tabs` | Identify which tab triggered permission |
| `scripting` | Inject detection scripts into web pages |
| `<all_urls>` | Monitor all websites for permission usage |

### Compliance
- ✅ GDPR compliant with no data sharing
- ✅ No cookies or tracking mechanisms
- ✅ Fully transparent open-source codebase

---

## 💼 Development Approach

This project was built with a focus on **accuracy and efficiency**. The core challenge was detecting permission usage in real-time, regardless of whether permissions were pre-granted or requested dynamically. 

The solution involved intercepting native browser APIs at the content script level, ensuring comprehensive monitoring without compromising user privacy or browser performance. This approach provides visibility into permission usage that standard Chrome APIs cannot offer.

---

## 🌟 Project Significance

Permission Analyzer addresses a critical gap in browser privacy tools. While browsers show when permissions are granted, they provide no visibility into when those permissions are actually used. This project demonstrates:

- Practical application of browser security concepts
- Advanced Chrome extension architecture (Manifest V3)
- Privacy-focused development principles
- Real-time API interception techniques
- Clean, maintainable code architecture

Built as a cybersecurity project to empower users with transparency and control over their digital privacy.

---


**Developed with a commitment to digital privacy and browser security.**
