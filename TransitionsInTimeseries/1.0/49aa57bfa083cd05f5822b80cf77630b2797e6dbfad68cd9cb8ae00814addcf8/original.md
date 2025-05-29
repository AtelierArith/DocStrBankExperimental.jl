```
SigmaSignificance(; factor = 3.0, tail = :both) <: Significance
```

A configuration struct for significance testing [`significant_transitions`](@ref). When used with [`ChangesResults`](@ref), significance is estimated by comparing how many standard deviations (`σ`) the value exceeds the mean value (`μ`). Values that exceed (if `tail = :right`) `μ + factor*σ`, or subseed (if `tail = :left`) `μ - factor*σ` are deemed significant. If `tail = :both` then either condition is checked.

`factor` can also be a vector of values, in which case a different value is used for each change metric.

See also [`QuantileSignificance`](@ref).
