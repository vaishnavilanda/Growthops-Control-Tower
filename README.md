# GrowthOps Control Tower — AI Campaign Reliability, Performance & Knowledge System

## Overview
I built the GrowthOps Control Tower to solve a major operational headache in marketing: campaign quality control, compliance checks, performance monitoring, experiment tracking, and documentation are usually handled in completely disconnected silos. 

This project is a modular n8n workflow powered by Anthropic Claude that connects all those pieces into a single, automated engine. It catches pre-launch errors, flags consent risks, diagnoses performance drops, prevents teams from running duplicate tests, and generates first-draft SOPs automatically.

---

## Problem vs. Solution

| The Traditional Marketing Ops Challenge | How GrowthOps Control Tower Solves It |
| :--- | :--- |
| **Manual & Inconsistent Pre-Launch QA:** Teams rely on manual checks, leading to broken tracking links, missing UTMs, or incorrect audience targeting hitting live campaigns. | **Automated Pre-Launch Validation:** Automatically checks campaign assets for broken links, missing UTMs, naming convention errors, and suppression conflicts before launch. |
| **Late Compliance Discovery:** Consent and suppression issues are often discovered too late—sometimes after complaints or compliance breaches occur. | **Proactive Compliance Audits:** Scans contact lists for conflicting consent values, missing sources, or suppressed contacts still enrolled in active flows. |
| **Reactive Performance Monitoring:** Performance anomalies and conversion drops are usually spotted long after budgets have been wasted. | **Real-Time Anomaly Detection & AI Diagnosis:** Monitors live metrics against baselines and uses Claude to instantly separate facts from hypotheses and suggest fixes. |
| **Repeated Unsuccessful Tests:** Experiment learnings are scattered or forgotten, causing marketing teams to repeat past failures without realizing it. | **Structured Experiment Memory:** Logs hypotheses, variables, and results in a searchable format to warn teams when a similar test has already failed. |
| **Scattered Documentation:** Workflow logic and campaign guidelines live in messy notes or disappear entirely when team members leave. | **Automated Documentation Agent:** Turns approved campaign definitions and workflow structures into clean, maintainable SOPs and handover notes. |

---

## The End-to-End Pipeline
Data flows through a controlled, multi-stage operations pipeline:

`Campaign Request / Live Data` $\rightarrow$ `Pre-Launch QA` $\rightarrow$ `Consent & Suppression` $\rightarrow$ `Performance & Anomaly Detection` $\rightarrow$ `Experiment Memory` $\rightarrow$ `Documentation`

1. **Module A — Pre-Launch QA:** Validates campaign links, UTM tags, naming conventions, preference links, and audience criteria.
2. **Module B — Consent & Suppression Audit:** Flags data and compliance risks, such as unsubscribed contacts receiving active campaigns or regional consent mismatches.
3. **Module C — Performance Monitoring:** Tracks live metrics (conversion drops, lead volume, CPA spikes) and uses Anthropic Claude to diagnose root causes, rank possible explanations, and assign next actions with a clear owner.
4. **Module D — Experiment Memory:** Stores structured records of past tests (hypothesis, audience, variable, result) and warns teams if a similar test was already run.
5. **Module E — Documentation Agent:** Automatically converts workflow and campaign structures into professional Markdown SOPs and handover documentation.

---

## Built-In Governance & Architecture
* **Shared Data Model:** All modules operate on a unified campaign and contact ID scheme to prevent data fragmentation.
* **Interpretable Baselines:** Uses simple, reliable thresholds (e.g., a 20% conversion rate drop) rather than overly complex predictive models to keep results transparent and easy to trust.
* **Structured AI Responses:** Claude outputs strict, structured JSON containing verified facts, hypotheses, and assigned owners for reliable n8n routing and alerting.

---

## Tech Stack
* **Orchestration:** n8n (cloud or self-hosted workflow engine)
* **AI Reasoning Layer:** Anthropic Claude API (structured JSON classification and root-cause analysis)
* **Data Sources (Prototype):** Sample campaign JSON/CSV records, contact lists with consent fields, and experiment history logs
* **Outputs:** Automated alerts (Slack/Email/Sheets), experiment logs, and Markdown documentation drafts

---

## Repository Structure
* `growthops_control_tower.json` — The complete, importable n8n workflow graph.
* `sample_campaign_dataset.json` — Sample campaign requests and tracking configurations.
* `sample_contact_list.json` — Contact records containing various consent and suppression states.
* `sample_experiment_log.json` — Historical test records used for experiment memory.

---

## Setup Instructions
1. Import `growthops_control_tower.json` directly into your n8n instance.
2. Configure your environment credentials for the **Anthropic Claude API** and **Google Sheets** (if using Sheets for logging).
3. Connect your sample data files or load the test payloads into the initial nodes.
4. Run a test execution to review the automated QA flags, Claude diagnostic alerts, experiment logs, and generated SOP drafts.
