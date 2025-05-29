```
auc(::roc; pfa=1.0, pmiss=1.0, normalize=true)
```

Computes the Area Under the Curve with a sense `auc → 0` indicating better performance.

Optional parameters `pfa` or `pmiss` limit integration over only part of the ROC curve. `normalize` indicates comparing the partial ROC to the trivial ROC.
