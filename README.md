🎓# BrightPath Academy - Student Performance Prediction System
📌 Problem Statement
BrightPath Academy collects extensive data on students' academic and extracurricular activities. However, the institution lacks a standardized platform to extract meaningful insights from this data. Key challenges include:

Inability to identify at-risk students in a timely manner.

Absence of personalized support strategies.

Limited understanding of the relationship between extracurriculars and academic success.

Underutilization of a rich reserve of student data.

💡 Solution
This project introduces a machine learning-based solution to predict academic performance and recommend individualized interventions. Using data from the Student_performance_data.csv, we:

Predict academic risk levels.

Recommend support strategies.

Compare multiple classification algorithms.

Deploy the most effective model through a web app built with Dash and hosted on Render.

🔍 Hypotheses
Hypothesis	Description
Study Time	More study time correlates with higher GradeClass.
Absences	More absences correlate with lower GradeClass.
Extracurriculars	Participation improves GradeClass.
Parental Support	Higher support is linked to better grades.
Tutoring	Tutored students perform better than untutored ones.

⚙️ System Setup
🔧 Tools Used
Visual Studio Code

Python

Git + GitHub

Render.com

Dash (Plotly)

🐍 Python Libraries
pandas, numpy – Data manipulation

matplotlib, seaborn – Visualization

scikit-learn – Machine learning models

xgboost, skopt – Gradient boosting and hyperparameter tuning

tensorflow – Deep learning

mord – Ordinal logistic regression

joblib – Model persistence

📂 Data Handling
📥 Data Import
python
Copy
Edit
import pandas as pd
df = pd.read_csv("Student_performance_data.csv")
🧠 Data Understanding
Used head(), info(), and describe() to explore dataset.

🧼 Cleaning
Removed irrelevant fields (e.g., StudentID)

Handled missing values and outliers (using IQR)

Created GradeClass from GPA:

A: ≥ 3.5

B: 3.0–3.49

C: 2.5–2.99

D: 2.0–2.49

F: < 2.0

📊 Exploratory Data Analysis (EDA)
✅ Univariate
Distribution analysis using histograms and boxplots

Focused on GradeClass

✅ Bivariate
Boxplots and Spearman correlation for ordinal vs. continuous features

Point-biserial correlation for binary vs. ordinal

Heatmaps for categorical comparisons

🤖 Machine Learning Models
🔸 Logistic Regression
Used StandardScaler, OrdinalEncoder, and SMOTE for balancing.

Implemented ordinal logistic regression using mord.LogisticAT.

Evaluated using classification report and confusion matrix.

🔸 Random Forest
Explored number of estimators and depth.

Trained on 2/3 split, tested on 1/3.

Benefits: Handles categorical variables and reduces overfitting.

🔸 XGBoost
Configured with multi:softprob objective.

Used sample_weight to handle imbalance.

Tuned with Bayesian optimization via skopt.

Achieved ~77% accuracy.

🧠 Deep Learning (ANN with CORAL)
Built using TensorFlow

Handled ordinal target using Cumulative Ordinal Regression with Logistic (CORAL)

Transformed ordinal target to binary thresholds

Evaluated using classification report and confusion matrix

🌐 Deployment
Platform
Web App built with Dash and deployed to Render

Pages
Home Page – Predicts GradeClass for inputted student data.

Analysis Page – Showcases EDA, model training, evaluation visuals.

Deployment Setup
Managed Python environment with rye and poetry

Model saved as .h5 file for loading into the app

Auto-deployment via GitHub-Render integration

📁 Project Structure
graphql
Copy
Edit
📦 brightpath-academy-ml
├── app/
│   ├── app.py              # Dash app
│   ├── home.py             # Home page layout
│   ├── analysis.py         # EDA and insights
├── models/
│   ├── best_model.h5       # Trained ANN with CORAL
├── notebooks/
│   ├── EDA.ipynb           # Data exploration and cleaning
│   ├── model_building.ipynb# Model comparison
├── data/
│   ├── Student_performance_data.csv
│   ├── Cleaned_Student_Performance_Data.csv
├── requirements.txt        # Libraries needed for deployment
├── README.md               # Project overview
└── .render.yaml            # Render deployment config
📈 Evaluation Metrics
Precision

Recall

F1 Score

Accuracy

Confusion Matrix

Each model’s performance was compared using the metrics above to determine the best model.

🧪 Conclusion
This project provides a robust ML pipeline to predict student academic risk and recommend proactive support. By deploying our most accurate and interpretable model with a user-friendly web app, BrightPath Academy can enhance its intervention strategies and improve student outcomes.

🙌 Contributors
Project Team @ BrightPath Academy

ML & Deployment Lead: [Your Name]
