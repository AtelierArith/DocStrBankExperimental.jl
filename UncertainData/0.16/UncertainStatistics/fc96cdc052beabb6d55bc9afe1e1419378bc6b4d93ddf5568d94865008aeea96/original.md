```
cor(x::AbstractUncertainValue, y::AbstractUncertainValue, n::Int)
```

Compute the Pearson correlation between two uncertain values by independently  drawing `n` samples from `x` and `n` samples from `y`, then computing  the Pearson correlation between those length-`n` draws.
