```
Dataframe(::Roc)
```

Converts a `Roc` object in a datframe with columns:

  * `pfa` the false alarm rate
  * `pmiss` the miss rate
  * `thres` the thereshold, separating this line's pfa and pmiss from the next
  * `chull` indicating if this point is on the convex hull of the ROC curve
  * `llr` the optimal log-likelihood-ratio score for all data points contributing to the ROC line segment from this line to the next
