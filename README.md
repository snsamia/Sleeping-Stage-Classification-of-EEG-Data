
# 🧠 Sleep Stage Classification from EEG Signals

![Pipeline Overview](https://github.com/snsamia/Sleeping-Stage-Classification-of-EEG-Data/blob/main/image.png)

## 📌 Overview

This project focuses on the classification of sleep stages (Wake, NREM, REM) using EEG data from the **Sleep PhysioNet EDF** dataset. It leverages classic machine learning techniques with spectral band power features, evaluating the model's ability to generalize across individual participants through **Leave-One-Participant-Out Cross-Validation (LOPO-CV)**.

---

## 📂 Dataset

- **Source**: [Sleep PhysioNet EDF](https://physionet.org/content/sleep-edfx/1.0.0/)
- **Access via**: `mne.datasets.sleep_physionet.age.fetch_data`
- **Sampling Rate**: 100 Hz (downsampled or filtered to 0.5–30 Hz range)
- **Annotations**: Wake (W), NREM stages (1–4), REM

---

## ⚙️ Methodology

### 1. Preprocessing
- EEG recordings are chunked into 30-second epochs
- Annotations are mapped to three classes: Wake, NREM, and REM

### 2. Feature Extraction
- Relative spectral power is extracted from 5 EEG frequency bands:
  - **Delta** (0.5–4.5 Hz)
  - **Theta** (4.5–8.5 Hz)
  - **Alpha** (8.5–11.5 Hz)
  - **Sigma** (11.5–15.5 Hz)
  - **Beta** (15.5–30 Hz)

### 3. Models Used
- ✅ Random Forest
- ✅ Logistic Regression
- ✅ Support Vector Machine (RBF Kernel)
- ✅ Gradient Boosting Classifier

### 4. Evaluation Strategy
- **Leave-One-Participant-Out Cross-Validation (LOPO-CV)**: Each participant is used once as a test set while the remaining serve as training data.
- Performance metrics: **Accuracy**, **Confusion Matrix**, **F1-Score**, **Precision**, **Recall**

---

## 📊 Results

- Achieved average classification accuracy of **~86% to ~93%**
- High performance on distinguishing Wake vs. NREM
- Random Forest and Gradient Boosting gave the best generalization across subjects

---

## 📦 Dependencies

```bash
pip install mne scikit-learn matplotlib numpy

