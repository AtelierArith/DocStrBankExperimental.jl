```
cov(x::AbstractUncertainValue, y::AbstractUncertainValue, n::Int; 
    corrected::Bool = true)
```

Compute the covariance between two uncertain values by independently  drawing `n` samples from `x` and `n` samples from `y` , then computing  the covariance between those length-`n` draws.
