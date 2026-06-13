# 🛡️ PK Escrow Sovereign Protocol

[![React Version](https://img.shields.io/badge/react-18%2B-blue.svg)](https://react.dev/)
[![Backend](https://img.shields.io/badge/backend-Express--Node.js-green.svg)](https://expressjs.com/)
[![Database](https://img.shields.io/badge/database-Firebase%20%26%20Firestore-orange.svg)](https://firebase.google.com/)
[![License](https://img.shields.io/badge/license-MIT-brightgreen.svg)](LICENSE)

**PK Escrow** is a secure, decentralized-feel, peer-to-peer (P2P) digital escrow payment platform specifically crafted for digital commerce, freelancing, and high-value trade markets. It directly bridges the trust gap between buyers and sellers, guaranteeing secure digital transaction loops, multi-factor security verifications, full dispute resolution frameworks, and lightweight offline-first testing options.

---

## 📌 Key Features

### 🌐 Seamless User Experience
*   **Intuitive Dual-Language Integration:** Fully English-first UI with toggle-ready local translation support to guide buyers, sellers, and agents step-by-step.
*   **Sovereign MPIN Security:** Protect accounts using custom mobile PIN protection, robust security questions, and cryptographically generated session keys.

### 🤝 Robust Escrow Mechanism
*   **Smart Dispute Resolution:** Real-time state management representing buyers, sellers, and neutral dispute administrators.
*   **Transaction Lifecycles:** Funds remain safely locked in escrow until the inspection period expires or the buyer confirms successful delivery.

---

## 🏗️ Technical Architecture

The project leverages a robust modern stack of modern React and Express server-side architecture to safely hide third-party API keys:

```
               +--------------------------------------+
               |             React SPA UI             |
               | (Vite, Tailwind, Lucide Icons, etc.)  |
               +------------------+-------------------+
                                  |
                        Secure REST API calls
                                  |
               +------------------v-------------------+
               |           Express Backend            |
               | (OTP Generation, Security, Routing)  |
               +---------+------------------+---------+
                         |                  |
              Firestore Admin SDK     Internal Cryptography
                         |                  |
               +---------v--------+   +-----v----------------+
               |  Cloud Database  |   | Unofficial WhatsApp  |
               |    (Firestore)   |   |        Gateway       |
               +------------------+   +----------------------+
```

*   **Frontend:** React 18 with Vite, absolute Tailwind CSS styling, responsive viewport adapters, and lightweight animations via Framer Motion.
*   **Backend:** Express.js engine acting as a secure proxy to preserve API key integrity and secure Firestore transactions from browser exploit surfaces.
*   **Database & Rules:** Custom Firebase Firestore database blueprint with isolated server-driven verification indexes (`whatsapp_otps/{phone}`).

---

## 🛡️ Escrow Transaction Lifecycle

PK Escrow safeguards funds by locking them under a secure ledger state-machine until verification conditions are satisfied:

1.  **Deal Creation:** The Buyer or Seller starts a transparent escrow agreement defining the price, product/service specifications, and delivery timeline.
2.  **Funds Assurance:** The Buyer initiates the payment transfer. Funds are safely locked in PK Escrow’s secure holding pool, triggering an automated status alert to the Seller.
3.  **Delivery & Inspection:** The Seller ships the items/completes the service. The Buyer gets an allocated timeframe to verify the quality and specs.
4.  **Instant Release or Dispute:**
    *   **Success Scenario:** The Buyer approves the delivery. Funds are released instantly to the Seller's linked bank or mobile wallet.
    *   **Dispute Scenario:** If issues arise, any party can initiate a dispute. Funds remain locked until a neutral platform moderator resolves the dispute based on evidence.

```
       [ Start Deal ] ──> [ Funds Locked ] ──> [ Delivery Period ]
                                                    │
                                  ┌─────────────────┴─────────────────┐
                           [ Buyer Approves ]                 [ Dispute Raised ]
                                  │                                   │
                           [ Release Funds ]                  [ Admin Decision ]
```

---

## 🚀 Quick Start & Installation

Follow these quick commands to bootstrap your sandbox development environment:

### 1. Repository Setup

```bash
git clone https://github.com/mohsinsmartshop/pk-escrow.git
cd pk-escrow
```

### 2. Install Project Dependencies

```bash
npm install
```

### 3. Setup Your Environment Variables (`.env`)

Create a `.env` file in your root folder:

```env
# Server Ingress Port (Default: 3000)
PORT=3000

# Firebase Configurations (Injects automatically on deployment)
FIREBASE_PROJECT_ID="pk-escrow-pay"

### 4. Run the Dev Engine

```bash
npm run dev
```

Your developer instance will live cleanly at `http://localhost:3000`.

---

## 🔒 Security Hardening Policies

*   **Rate Limiting Protection:** Prevent endpoint abuse with standard sliding rate-limiting windows.
*   **Replay Attack Protection:** All generated tokens are single-use only. Once an OTP is processed (validated or invalidated due to time-to-live), the database record is immediately purged to eliminate reuse surfaces.
*   **Zero-Exposure API Proxy:** Third-party gateway credentials, tokens, and instance hooks are resolved strictly at server-side to prevent browser exposure.

---

## 🤝 Contributing

We welcome contributions from software engineers, FinTech experts, and designers!

1. Fork the Project.
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`).
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`).
4. Push to the Branch (`git push origin feature/AmazingFeature`).
5. Open a Pull Request.

---

<p align="center">Made with ❤️ for the PK Digital Escrow Ecosystem.</p>


PK Escrow — Project One-Pager
​1. The Hook 
"A secure peer-to-peer (P2P) digital escrow platform designed to eliminate fraud and build absolute trust between online buyers and sellers across Pakistan."
​2. The Problem: 
"There's a big trust deficit in online peer-to-peer (P2P) buying, selling, and freelancing. Buyers worry that the seller might block them after sending the money, and sellers worry that the buyer might not pay after receiving the work/product.".
​Trust Deficit: There isn't any easy and secure third-party escrow system in the market that an average user can use without going through complicated verification..
​Financial Loss:Every year thousands of people fall victim to online scams because there’s no security with advance payments..
​3. The Solution: 
The buyer's money stays in your secure wallet until the seller delivers the product. 
Milestone-Based Release: As soon as delivery is confirmed, the funds automatically get transferred to the seller. If there's a scam, you can raise a dispute and get a refund.
​We have made a smart escrow application that acts as a 'Trusted Middleman' between the buyer and the seller.
​Escrow Logic: The buyer's money stays in your secure wallet until the seller delivers the product. 
Milestone-Based Release: As soon as delivery is confirmed, the funds automatically get transferred to the seller. If there's a scam, you can raise a dispute and get a refund.
​4. Technical Architecture & Tech Stack
​"PK Escrow is a secure peer-to-peer (P2P) digital escrow platform built with React, Node.js, Express, and Firebase/Firestore that eliminates online buyer-seller fraud in Pakistani e-commerce through safe ledger lifecycles and highly hardened cybersecurity verification protocols."
​5. Current Status (The MVP is Live!)
​We have fully prepared its working prototype (MVP). Core flow is working: user registration, escrow wallet creation, database read/write logic, and the basic transaction state machine are all fully functional.
​6. The Request:
​We are looking for funding, grants, or cloud credits to scale this project so that:
Database & Servers: We can buy backend hosting and production-grade database limits to handle live traffic.
Security Audits: Since it's a fintech application, we can further tighten database security.
