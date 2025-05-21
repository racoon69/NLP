#  Medical NLP: Misspelling Correction in Clinical Transcriptions 

This project addresses the real-world challenge of **misspellings in medical transcriptions** using Natural Language Processing (NLP). We implement a dictionary-based spell correction method using **SymSpell**, capable of correcting noisy and distorted medical terms with high efficiency and low computational cost.

---

##  Project Overview 

- **Objective:** Automatically correct spelling mistakes in medical transcriptions.
- **Approach:** Use SymSpell (edit-distance spell checker) and evaluate its accuracy.
- **Dataset:** MTSamples — real-world medical transcription dataset from Kaggle.
- **Evaluation Metric:** BLEU Score to compare corrected text against original text.

---

##  Project Structure
###  Problem Statement 

Medical documentation often contains spelling errors due to fast-paced clinical environments and complex terminology. Misspellings in such records can negatively impact:
- Patient safety (e.g., wrong drug names)
- Clinical decision-making
- NLP downstream tasks like named entity recognition

Correcting such errors is critical in pre-processing pipelines for reliable analysis.

---

###  NLP Methodology 

- **Preprocessing:** Lowercasing, punctuation removal, and whitespace normalization.
- **Synthetic Error Injection:** Character swaps in ~30% of words simulate real-world typos.
- **Correction Engine:** [SymSpell](https://github.com/wolfgarbe/SymSpell) with a standard English frequency dictionary.
- **Evaluation:** BLEU Score (1-gram + smoothing) to assess how closely corrected text matches the original.

---

###  Dataset 

- **Name:** MTSamples - Medical Transcriptions
- **Source:** [Kaggle - Medical Transcriptions Dataset](https://www.kaggle.com/datasets/tboyle10/medicaltranscriptions)
- **Size:** ~5,000 real-world clinical transcription samples
- **Usage:** 10-sample subset used for demonstration due to resource constraints

---

###  Workflow 

1. Load dataset (`mtsamples.csv`)
2. Clean and normalize transcription text
3. Inject spelling errors to simulate transcription noise
4. Correct misspelled words using SymSpell
5. Evaluate corrections using BLEU score

---

###  Evaluation 

- **Metric:** BLEU Score (1-gram with smoothing)
- **Average BLEU Score:** `0.65`
- **Interpretation:** The model accurately restored misspelled terms in most cases, especially frequent or domain-relevant words. Performance was slightly lower on rare or severely distorted terms.

#### Example 
| Clean Text | Misspelled | Corrected | BLEU |
|------------|------------|-----------|------|
| ...present illness the patient is... | ...Persent ilnless the paitent is... | ...present illness the patient is... | 0.77 |
| ...endstage renal disease... | ...renal disaese... | ...renal disease... | 0.57 |
| ...preprocedure diagnosis chest pain... | ...diagnoiss cehst pain... | ...diagnosis chest pain... | 0.56 |

---

### Getting Started 
1. Open the 'NLP_asg3_final.ipynb' notebook in google colab
2. Upload 'mtsamples.csv' to the same folder in your Google Drive
3. Follow the steps in the notebook to clean, corrupt, correct, and evaluate the data
4. Review final output in 'corrected_transcriptions_output.csv'

---
### Technologies 
- Python (3.x)
- Google Colab
- 'pandas', 're', 'random'
- 'symspellpy' for correction
- 'nltk' for BLEU scoring

---
###License 
This project is developed for academic use only. The sataset used is publicaly available under terms provided by kaggle. 

---
### Team Members
- **Dalia Mohamed:** Data preparation, SymSpell integration, BLEU evaluation
---
### Acknowlegements 
- [SymSpell Algorithm] (https://github.com/wolfgarbe/SymSpell) by Wolf Garbe
- Dataset from [MTSamples on Kaggle] (https://www.kaggle.com/datasets/tboyle10/medicaltranscriptions)
- BLEU evaluation via 'nltk'
