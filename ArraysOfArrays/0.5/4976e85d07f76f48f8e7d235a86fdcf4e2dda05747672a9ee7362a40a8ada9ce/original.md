```
mean(X::AbstractVectorOfSimilarArrays)
mean(X::AbstractVectorOfSimilarArrays, w::StatsBase.AbstractWeights)
```

Compute the mean of the elements vectors of `X`. Equivalent to `mean` of `flatview(X)` along the last dimension.
