# 🧩 Data Anomaly Detection Project

## 📘 Overview

This mini-project simulates a **data validation task**, similar to what a GPU/CPU validation engineer might do at Intel. The goal is to identify **regressions or anomalies** in a dataset — unexpected drops or spikes — which may indicate performance issues or software bugs.

The project uses **benchmark data over 50 days** to demonstrate:

- Analytical thinking
- Attention to subtle irregularities
- Data visualization and interpretation

---

## 🎯 Objective

1. Load benchmark data (`performance_data.xlsx`) containing 50 test points.
2. Detect anomalies based on statistical thresholds.
3. Visualize benchmark trends with anomalies highlighted.
4. Summarize findings in a concise interpretation.

---

## 🧰 Tools & Technologies

- **Python 3.x**  
- **pandas** — for data handling  
- **matplotlib** — for visualization  
- **Excel (.xlsx)** — input dataset  

---


## 🧮 Python Code

```python
import pandas as pd
import matplotlib.pyplot as plt

# Load dataset
file_path = "/home/nusrat/Desktop/Spreadsheet/performance_data.xlsx"
df = pd.read_excel(file_path)

# Calculate mean and standard deviation
mean = df["Benchmark_Score"].mean()
std_dev = df["Benchmark_Score"].std()

# Define anomaly thresholds
upper_limit = mean + 2*std_dev
lower_limit = mean - 2*std_dev

# Flag anomalies
df["Anomaly"] = df["Benchmark_Score"].apply(lambda x: "Anomaly" if x < lower_limit or x > upper_limit else "Normal")

# Print anomalies
print("=== Detected Anomalies ===")
print(df[df["Anomaly"] == "Anomaly"])

# Plot benchmark trend with anomalies
plt.figure(figsize=(10,6))
plt.plot(df["Day"], df["Benchmark_Score"], marker='o', linestyle='-', color="blue", label="Benchmark Score")
plt.axhline(mean, color="green", linestyle="--", label="Mean")
plt.axhline(upper_limit, color="orange", linestyle="--", label="Upper Limit")
plt.axhline(lower_limit, color="red", linestyle="--", label="Lower Limit")

# Highlight anomalies
anomalies = df[df["Anomaly"] == "Anomaly"]
plt.scatter(anomalies["Day"], anomalies["Benchmark_Score"], color="red", s=100, label="Anomaly")

plt.title("Data Anomaly Detection - Benchmark Results")
plt.xlabel("Day")
plt.ylabel("Benchmark Score")
plt.legend()
plt.grid(True)
plt.tight_layout()
plt.show()

```

---
## 📊 Dataset Example

| Day | Benchmark_Score |
|-----|-----------------|
| 1   | 98.4            |
| 2   | 99.1            |
| 3   | 100.2           |
| ... | ...             |
| 50  | 101.3           |

> The dataset contains **50 benchmark points** with a few anomalies (spikes or drops) introduced to simulate regressions.

---
## 📈 Visualization

The Python script generates a line chart with:

- **Blue line** → Benchmark trend over 50 days  
- **Green dashed line** → Mean score  
- **Red/Orange dashed lines** → Lower and upper statistical thresholds  
- **Red dots** → Detected anomalies
---
## 🧾 Data Interpretation (Example)

- On certain days, benchmark scores dropped significantly below the average trend, indicating potential regressions.  
- These anomalies could be caused by hardware fluctuations, software issues, or external interference during testing.  
- Overall, most data points remain stable, but anomalies are clearly flagged for further investigation.
---
## 🚀 Key Skills Demonstrated

| Skill               | Description                                           |
|---------------------|-------------------------------------------------------|
| Analytical Thinking | Detect anomalies using statistical thresholds.       |
| Data Visualization  | Line charts highlight regressions clearly.           |
| Attention to Detail | Identifying subtle deviations in performance data.  |
| Technical Reporting | Summarizing insights concisely for stakeholders.    |


---

## 🏁 Conclusion

This project demonstrates how to detect and visualize anomalies in benchmark data, mimicking tasks performed by validation engineers in GPU/CPU performance testing. It showcases analytical skills and systems thinking.

---





