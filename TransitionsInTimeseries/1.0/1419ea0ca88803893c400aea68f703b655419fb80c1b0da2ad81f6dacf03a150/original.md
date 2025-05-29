```
QuantileSignificance(; p = 0.95, tail = :both) <: Significance
```

A configuration struct for significance testing [`significant_transitions`](@ref). When used with [`ChangesResults`](@ref), significance is estimated by comparing the value of each change metric with its `p`-quantile. Values that exceed the `p`-quantile (if `tail = :right`) or subseed the `1-p`-quantile (if `tail = :left`) are deemed significant. If `tail = :both` then either condition is checked.

`QuantileSignficance` guarantees that some values will be significant by the very definition of what a quantile is. See also [`SigmaSignificance`](@ref) that is similar but does not have this guarantee.
