# IEC 62443 OT Security Requirements Dataset (v1.0)

This repository provides a structured dataset of 4,497 expert-curated, programmatically generated OT (Operational Technology) security requirements, produced from IEC 62443-aligned templates and validated for domain realism across the IEC 62443-3-3 Functional Requirement families (FR1–FR7). Requirements are generated for three industrial device categories:

- **PLC** – Programmable Logic Controller  
- **HMI** – Human–Machine Interface  
- **Drive** – Industrial Drive / Motion Controller  

The dataset is designed for **LLM benchmarking**, **automated cybersecurity requirement classification**, **research on FR reasoning**, and **OT-focused AI evaluation**.

---

## ✨ Key Features

### ✔ 4,497 Requirements (Structured JSON)
Each requirement entry contains:

- `id` – global neutral unique ID (e.g., `R00001`)
- `local_id` – device-specific incremental ID
- `device` – {PLC, HMI, Drive}
- `FR` – one of FR1–FR7 (primary Functional Requirement)
- `FR_name` – full IEC 62443 FR title
- `text` – natural-language security requirement

Files included:

- `requirements_PLC.json`
- `requirements_HMI.json`
- `requirements_Drive.json`
- `requirements_all.json`

---

### ✔ Sphinx-Needs Compatible Requirements (Documentation-as-Code)

All requirements are also exported using Sphinx-Needs `.. req::` directives:

- `requirements_PLC_needs.rst`
- `requirements_HMI_needs.rst`
- `requirements_Drive_needs.rst`
- `requirements_all_needs.rst`

These files integrate seamlessly with **Sphinx**, **Sphinx-Needs**, and **Docs-as-Code pipelines**, enabling:

- Traceability diagrams  
- Requirement filtering and queries  
- Tables grouped by FR or device  
- Integration into safety/security documentation workflows  

---

## 📘 Dataset Generation Method

The dataset was generated using:

- A **single structured template file**: `fr_templates_devices.json`
- A Python script that performs **Cartesian expansion** over:
  - Templates
  - Subjects
  - Actions
  - Objects
  - Conditions
  - Device-specific FR configurations

This ensures:

- High coverage of IEC 62443 FR semantics  
- Linguistic diversity  
- Device-appropriate requirement phrasing  
- Realistic OT cybersecurity terminology  

The requirements follow IEC 62443-3-3 FR structure:

| FR | Name |
|----|-------------------------------|
| FR1 | Identification & Authentication Control |
| FR2 | Use Control |
| FR3 | System Integrity |
| FR4 | Data Confidentiality |
| FR5 | Restricted Data Flow |
| FR6 | Timely Response to Events |
| FR7 | Resource Availability |

Because several FR families overlap conceptually (e.g., FR3↔FR6, FR2↔FR5, FR5↔FR7), the dataset naturally contains **realistic ambiguity** found in actual OT security engineering.

---

## 🔬 Benchmarking Purpose

This dataset is intended **exclusively for evaluation (not training)**.

### Recommended LLM benchmarking tasks:

#### **Task T1 — FR Classification (7 classes)**  
Input: Requirement text  
Output: FR1–FR7  

#### Recommended prompting conditions:
- **Zero-shot**
- **Few-shot**
- **Rule-based**
- **Chain-of-thought (optional)**

Suggested decoding:  
`temperature=0`, `top_p=1`, deterministic outputs.

---

## 📊 Evaluation Metrics

The following metrics are recommended:

- **Accuracy**
- **Macro F1-score** (balanced FR evaluation)
- **Per-FR accuracy / difficulty score**
- **Confusion matrix**
- **Strict (gold) vs lenient (silver) accuracy**

Ambiguity-aware evaluation (silver) can be enabled through:

- Secondary FR labels  
- FR adjacency mappings (neighboring categories)  

---
-Will be updated soon
