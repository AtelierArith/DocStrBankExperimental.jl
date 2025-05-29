```
var(X::AbstractVectorOfSimilarArrays; corrected::Bool = true)
var(X::AbstractVectorOfSimilarArrays, w::StatsBase.AbstractWeights; corrected::Bool = true)
```

Compute the sample standard deviation of the elements vectors of `X`. Compute the sample variance of the elements vectors of `X`. Equivalent to `std` of `flatview(X)` along the last dimension.
