```
cov(X, w::AbstractWeights, vardim=1; mean=nothing, corrected=false)
```

Compute the weighted covariance matrix. Similar to `var` and `std` the biased covariance matrix (`corrected=false`) is computed by multiplying `scattermat(X, w)` by $\frac{1}{\sum{w}}$ to normalize. However, the unbiased covariance matrix (`corrected=true`) is dependent on the type of weights used:

  * `AnalyticWeights`: $\frac{1}{\sum w - \sum {w^2} / \sum w}$
  * `FrequencyWeights`: $\frac{1}{\sum{w} - 1}$
  * `ProbabilityWeights`: $\frac{n}{(n - 1) \sum w}$ where $n$ equals `count(!iszero, w)`
  * `Weights`: `ArgumentError` (bias correction not supported)
