```
roc_curve(ŷ, y) -> false_positive_rates, true_positive_rates, thresholds
```

Return data for plotting the receiver operator characteristic (ROC curve) for a binary classification problem.

Here `ŷ` is a vector of `UnivariateFinite` distributions (from CategoricalDistributions.jl) over the two values taken by the ground truth observations `y`, a `CategoricalVector`. 

If there are `k` unique probabilities, then there are correspondingly `k` thresholds and `k+1` "bins" over which the false positive and true positive rates are constant.:

  * `[0.0 - thresholds[1]]`
  * `[thresholds[1] - thresholds[2]]`
  * ...
  * `[thresholds[k] - 1]`

Consequently, `true_positive_rates` and `false_positive_rates` have length `k+1` if `thresholds` has length `k`.

To plot the curve using your favorite plotting backend, do something like `plot(false_positive_rates, true_positive_rates)`.

Core algorithm: [`Functions.roc_curve`](@ref)

See also [`AreaUnderCurve`](@ref). 
