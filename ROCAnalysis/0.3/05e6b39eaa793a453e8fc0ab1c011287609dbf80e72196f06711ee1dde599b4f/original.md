```
AUC(::roc; pfa=1.0, pmiss=1.0, normalize=true)
```

computes the traditional Area Under the Curve with a sense `AUC → 1` indicating better performance.

Roughly, we have `AUC(args) == 1 - auc(args)`.

Optional parameters `pfa` or `pmiss` limit integration over only part of the ROC curve. `normalize` indicates comparing the partial ROC to the trivial ROC.

You can also call this function as `AUC(targets::Vector, nontargets::Vector; kwargs...)`
