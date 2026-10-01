<!--
  Hey! This README is written to match your notebook (JobTrap_AI_LSTM.ipynb).
  Anything in [square brackets] is something only you know, so fill it in before you push.
  These comment lines are invisible on GitHub, so feel free to delete them when you're done.
-->

# 🛡️ JobTrap AI

**Fake Job Message Pattern Detector using an LSTM (RNN-based NLP)**

> Don't fall for fake offers. Let AI detect the warning signs.

<!-- Short and friendly intro. A reader should understand the whole project in these three lines. -->
JobTrap AI reads a recruitment message and tells you whether it looks **suspicious** or **legitimate-like**. It also points out the warning signs it noticed, such as a payment request, an OTP demand, or fake urgency.

It is built as an academic NLP project (Academic Assignment 2) at Thiagarajar College of Engineering.

---

## 🤔 Why this project?

<!-- Keep this personal and simple. Judges and recruiters read this part first. -->
Students and fresh graduates get a lot of job messages, and some of them are scams. They usually ask for a "registration fee", promise a job with no interview, or push you to act immediately. JobTrap AI gives job seekers a quick first warning before they pay or share anything.

> **Example:** *"Congratulations! You are selected. Pay ₹2,000 registration fee to confirm your job."* → flagged as suspicious.

---

## ✨ What it does

- Classifies a message as **Suspicious** or **Legitimate-like** using an LSTM.
- Shows the model's **suspicious probability** for the message.
- Lists the **warning patterns** it found: payment request, personal information request, urgency and unrealistic job promise.
- Includes a simple interactive demo where you type any message and get a result.
- Saves the trained model as `jobtrap_ai_lstm.keras` so you can reuse it.

<!-- Note for you: the pattern detection is rule-based (keyword matching), not learned by the LSTM. It is kept honest here on purpose. -->
> The warning-pattern list comes from a simple keyword check that runs next to the model. The LSTM itself only produces the suspicious/legitimate prediction.

---

## 🧠 How it works

```
Input message
   ↓
Text cleaning (lowercase, remove symbols, trim spaces)
   ↓
Tokenization + padding (vocab 5,000 words, length 40)
   ↓
Embedding layer (64 dimensions)
   ↓
LSTM layer (64 units)
   ↓
Dropout (0.4)
   ↓
Dense layer (1 unit, sigmoid)
   ↓
Suspicious (1) / Legitimate-like (0)
```

| Setting | Value |
|---|---|
| Vocabulary size | 5,000 words (with an `<OOV>` token) |
| Sequence length | 40 tokens (post-padding and post-truncating) |
| Embedding size | 64 |
| LSTM units | 64 |
| Dropout | 0.4 |
| Output | 1 neuron with sigmoid, threshold 0.5 |
| Loss | Binary crossentropy |
| Optimizer | Adam |
| Epochs / batch size | 8 / 64 |
| Validation split | 20% of the training data |

---

## 📦 Dataset

<!-- Be upfront about this. A reviewer who sees "synthetic" explained clearly trusts you more than one who finds out later. -->
The notebook uses a **synthetic dataset of 20,000 messages** generated in code from message templates with random amounts, days and times:

- **10,000 suspicious** messages (label `1`): fee requests, OTP and bank detail requests, "no interview" promises, urgent pressure.
- **10,000 legitimate-like** messages (label `0`): interview schedules, portal instructions, application status updates.

The data is shuffled with `random_state=42`, and the generator is seeded with `random.seed(42)`, so results are reproducible.

<!-- If you later switch to a real dataset such as Fake Job Postings (EMSCAD) on Kaggle, update this section and the numbers below. -->

---

## 📊 Results

<!-- Run the notebook, then copy your real numbers from the evaluation cells. Please don't leave guesses here. -->

| Metric | Value |
|---|---|
| Test accuracy | [fill from notebook] |
| Test loss | [fill from notebook] |
| Precision / Recall / F1 | [fill from classification report] |
| Training / test samples | [fill from the final summary cell] |

**Training curves and confusion matrix:** [add screenshots to an `images/` folder and link them here, for example `![Accuracy](images/accuracy.png)`]

---

## 🚀 Getting started

<!-- These steps are for someone who has never seen your project. Test them once on a fresh Colab. -->

**1. Clone the repo**
```bash
git clone [your-repo-url]
cd [your-repo-folder]
```

**2. Install the libraries**
```bash
pip install numpy pandas matplotlib scikit-learn tensorflow
```

**3. Run the notebook**

Open `JobTrap_AI_LSTM.ipynb` in Google Colab or Jupyter and run the cells from top to bottom.

**4. Try the demo**

The last section of the notebook asks you to type a recruitment message and returns the prediction with any warning patterns.

---

## 🗂️ Project structure

```
JobTrap-AI/
├── JobTrap_AI_LSTM.ipynb   # full pipeline: data → model → evaluation → demo
├── jobtrap_ai_lstm.keras   # saved model (created after running the notebook)
├── images/                 # result screenshots for this README
└── README.md
```

---

## 🛠️ Built with

Python · Google Colab · TensorFlow / Keras · NumPy · Pandas · scikit-learn · Matplotlib

---

## ⚠️ Limitations

<!-- Honest limitations make a project look mature, not weak. Keep this section. -->
- The training data is **synthetic and template-based**, so the model has seen a small set of sentence patterns. Scores on this data will look very high and **will not carry over to real-world messages** that are worded differently.
- JobTrap AI looks at **language patterns only**. It does not verify employers, links, phone numbers or company websites.
- It gives an **initial warning, not a guarantee**. A "legitimate-like" result does not mean a job offer is genuine, so always verify the company independently.

## 🔮 Future work

- Train and test on real labelled recruitment messages.
- Support SMS, email and social media messages.
- Highlight the exact words that triggered the warning.
- Build a small web app so anyone can use it without running a notebook.

---

## 👥 Team

<!-- Replace with real names and roles. Link your GitHub profiles if you like. -->

| Name | Role |
|---|---|
| [Member 1] | [e.g., Dataset & preprocessing] |
| [Member 2] | [e.g., Model building & training] |
| [Member 3] | [e.g., Evaluation, demo & poster] |

Department of [Department], Thiagarajar College of Engineering

---

<!-- Add a LICENSE file to the repo and name it here. MIT is a common, simple choice for student projects. -->
📄 License: [add license]
