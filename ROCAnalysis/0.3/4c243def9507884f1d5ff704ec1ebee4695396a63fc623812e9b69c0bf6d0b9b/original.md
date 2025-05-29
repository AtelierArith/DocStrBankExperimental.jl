```
minber()
```

Computes the minimum Byes Error Rate for a set of scores, found after an optimal score-to-llr (log-likelihood-ratio) transformation. The optimal transformation corresponds to the convex hull of the ROC, where the optimal llr values correspont to the negative log of the slope of the appropriate line segment spanning the ROC.  This is equivalent to running the pool-adjacent-violators algorithm on the test data.

In order to compute `minber()` for multiple cost functions, as in a Normalized Bayes Error Rate plot, it is advantageous to compute a `Roc` object once.

Arguments: see `ber()`.
