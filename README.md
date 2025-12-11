# Spam Detection Using a Multilayer Perceptron (MLP)

This project builds a **spam classification model** using a **Multilayer Perceptron (MLP)** neural network trained on SMS text messages. The goal is to distinguish between **spam** and **ham (legitimate)** messages using TF–IDF vectorisation combined with a neural network classifier.

The complete methodology and analysis follow the assignment report. :contentReference[oaicite:1]{index=1}

---


## 📦 Dataset

The project uses **spam.csv**, which contains:

- SMS message text  
- Labels: `"ham"` (legitimate) or `"spam"`

### Dataset Notes
- The dataset is **imbalanced** (more ham than spam).  
- This makes precision and recall more meaningful than accuracy.  
- TF–IDF is used to convert raw text into numeric vectors for the MLP.

More details are shown in the report’s dataset overview and frequency chart. 

---

## 🧠 Methodology

### 1️⃣ Preprocessing
- Remove empty/unused columns  
- Convert text to string  
- Drop missing rows  

### 2️⃣ TF–IDF Vectorisation
TF–IDF converts SMS messages into a sparse feature matrix by:

- Counting important words  
- Down-weighting very common words  
- Representing text in numeric form for NN training

### 3️⃣ Train–Test Split
- 80% training  
- 20% testing  
- **Stratified** to maintain the ham/spam ratio

### 4️⃣ MLP Model

| Parameter | Value |
|----------|--------|
| Hidden units | 64 |
| Activation | ReLU |
| Optimizer | Adam |
| Max iterations | 20 |
| Random state | 42 |

The TF–IDF vectoriser and MLP are combined into a **single Scikit-learn Pipeline**.

---

## 📈 Results

The model demonstrates strong performance:

| Metric | Result |
|--------|--------|
| Accuracy | > 95% (typical) |
| Precision | High for both classes |
| Recall | Slightly lower for spam |

### Key Observations
- Very few ham → spam errors  
- Some spam → ham errors (false negatives), especially for borderline messages  
- The confusion matrix (see report) shows good separation between classes   

---

## 🧪 Discussion

### Strengths
- Learns nonlinear patterns in text  
- Works well with short, informal messages  
- TF–IDF + MLP is fast and computationally light  

### Limitations
- Slight under-detection of spam due to class imbalance  
- MLP lacks semantic understanding  
- Low training iterations (20) may limit learning depth  

### Future Improvements
- Increase training iterations  
- Use class weighting or oversampling  
- Try deep-learning models (LSTM, GRU, BERT)  
- Add stemming/lemmatisation before vectorisation  

---

## ⚖️ Ethical Considerations

- False negatives (spam predicted as ham) can expose users to harmful content  
- Dataset contains sensitive messages → privacy and data governance required  
- Spam filters must avoid censoring legitimate communication  
- Machine learning should assist, not replace, human judgment  

---

## 📚 References

- Scikit-learn Documentation  
- Almeida et al. (2011), SMS Spam Collection Dataset  
- Course lecture notes and supporting material  

---

## 🔗 GitHub Repository
https://github.com/shivanibashetty14/Machine-Learning-Individual.git

---

## 📝 License

This project is released under the MIT License — see the LICENSE file for details.

