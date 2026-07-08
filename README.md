# Waiver---PS-
Here is a clean GitHub project description in 300 words:

---

## Waiver Prediction Optimizer — Cholamandalam Finance

### Overview
This project builds a data-driven waiver prediction model for loan customers at Cholamandalam Finance. The model predicts three types of waivers — Interest Rate Waiver (W1), Admin Fee Waiver (W2), and Sourcing Fee Waiver (W3) — for 20,000 loan customers using a constrained optimization framework.

### Problem Statement
Waiver decisions in lending are often manual and inconsistent. Different officers give different discounts to similar customers. This project replaces that subjectivity with a systematic, explainable scoring model that produces consistent waiver predictions while respecting all business rules.

### Approach
Every customer is assigned to one bucket across five dimensions using explicit rule-based conditions:
- **A** — Customer Type (Personal / Commercial)
- **B** — Repayment History and Loyalty (12 buckets based on DPD, prior waiver bands, and Δoh)
- **C** — Lead Source and Dealership Quality (38 buckets using a 6×6 LF% × DP% grid)
- **D** — Branch Performance (4 buckets based on profitability and disbursal targets)
- **E** — Geography (5 buckets based on branch competitive category)

The model finds the best score for each of the 61 bucket states and the best weights for each waiver type using Multi-Start SLSQP — a constrained mathematical optimizer that runs from 5 different starting points and picks the best result.

### Key Features
- 76 optimized parameters (61 bucket values + 15 weights)
- 21 business rules enforced (B1=5, B2=0, A1>A2, ordering constraints, weights sum to 1)
- All 15 weights constrained to be greater than 0.05
- 80/20 train-test split with no overfitting (Train RMSE = 0.0136, Test RMSE = 0.0135)
- Methods compared — Single SLSQP, Multi-Start SLSQP, Ridge Regression
- Structured Excel output with 5 sheets including condition summary, weights, and validation

### Technologies Used
Python, NumPy, Pandas, SciPy, Scikit-learn, OpenPyXL
