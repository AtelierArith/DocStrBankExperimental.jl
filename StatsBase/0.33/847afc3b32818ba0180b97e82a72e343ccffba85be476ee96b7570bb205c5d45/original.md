```
mean!(R::AbstractArray, A::AbstractArray, w::AbstractWeights[; dims=nothing])
```

Compute the weighted mean of array `A` with weight vector `w` (of type `AbstractWeights`) along dimension `dims`, and write results to `R`.
