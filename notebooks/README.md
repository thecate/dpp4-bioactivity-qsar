# DPP-4 Bioactivity QSAR (ChEMBL IC50 → pIC50)

## Overview
This project builds QSAR models to predict **DPP-4 inhibitor bioactivity** using ChEMBL IC50 data.
The workflow demonstrates an end-to-end, industry-relevant cheminformatics pipeline:
- Retrieve and curate public bioactivity data
- Convert IC50 (nM) to **pIC50**
- Train descriptor and ECFP fingerprint models
- Evaluate with both random split and **Murcko scaffold split** (chem-aware validation)

---

## Dataset
- Source: **ChEMBL**
- Target: **DPP-4 (CHEMBL284, Homo sapiens)**
- Endpoint: **IC50 (nM)** converted to **pIC50**

Saved to: `data/dpp4_ic50_clean.csv`

---

## Methodology
### Features
- **Descriptors**: MolWt, LogP, TPSA, HBD, HBA, Rotatable Bonds, Rings
- **Fingerprints**: **ECFP4** (Morgan radius=2, 2048 bits)

### Models
- Random Forest Regressor

### Validation
- **Random split** (interpolation; analogue bias possible)
- **Scaffold split** (Murcko scaffolds; tests generalization to new chemotypes)

---

## Results
Metrics are saved in `reports/dpp4_metrics.json`.

Key observations:
- Descriptor and ECFP models perform comparably on random split
- Performance drops under scaffold split (expected and realistic)
- Scaffold split provides a more honest estimate of real-world generalization

Parity plot:
- `reports/figures/dpp4_parity_random.png`

---

## Project Structure

project-2/
├── data/
├── notebooks/
├── models/
└── reports/
└── figures/


---

## Tools & Technologies
- Python, RDKit
- pandas, scikit-learn
- ChEMBL webresource client
- Jupyter Notebook
- Git & GitHub

---

## Author
Theresia Cate  
Dr. rer. nat in Chemistry
