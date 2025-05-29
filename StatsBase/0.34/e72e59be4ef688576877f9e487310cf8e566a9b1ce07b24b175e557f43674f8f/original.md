```
cov2cor(C::AbstractMatrix, [s::AbstractArray])
```

Compute the correlation matrix from the covariance matrix `C` and, optionally, a vector of standard deviations `s`. Use [`StatsBase.cov2cor!`](@ref) for an in-place version.
