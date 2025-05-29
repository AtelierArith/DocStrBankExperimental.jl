```
quantile(d::AbstractUncertainValueDataset, p, n::Int; kwargs...)
```

Compute element-wise quantile(s) `p`of a dataset consisting of uncertain values. Takes the quantiles of an `n`-draw sample for each element.
