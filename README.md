# 🧠 Lookahead KMeans: Smarter Cluster Initialization

This repo implements and compares a **lookahead-based initialization** strategy for KMeans against standard `k-means++`. The lookahead approach generates multiple candidate initializations and runs a few KMeans steps (not the full algorithm) for each. It then selects the initialization that produces the best intermediate silhouette score after this limited rollout.

## 🔍 What’s Inside

* 📆 Evaluates both `k-means++` and **lookahead init**
* 📈 Tracks **silhouette scores** over iterations
* ⏱ Measures **runtime** and **peak memory**
* 🧪 Tested on real (Iris, Wine) and synthetic datasets (Overlapping, Noisy)

## Notebook

[Notebook](lookahead-kmeans.ipynb)

## 🧠 Lookahead Strategy

* Randomly initialize multiple candidate centroids
* For each, simulate several KMeans steps (rollout_depth)
* Pick the one with the best silhouette score

## 📈 Results

| Dataset | Std Sil. | LA Sil. | Std Time | LA Time | Std Mem | LA Mem  |
| ------- | -------- | ------- | -------- | ------- | ------- | ------- |
| Iris    | 0.55     | 0.55    | 0.05 s   | 0.12 s  | 0.36 MB | 0.36 MB |
| Noisy   | 0.18     | 0.23    | 0.13 s   | 0.31 s  | 2.01 MB | 2.00 MB |

## 📪 When to Use

* Useful for **noisy** or **high-dimensional** data
* Helps when **initialization quality matters**
* Offers better clustering at the cost of runtime

