```
kmeans(X::AbstractMatrix{<:Real}, r::AbstractVector{Int},
    c::AbstractVector{Int}, μ::AbstractMatrix{<:Real}; <keyword arguments>)
```

Cluster the data `X` with the $k$-means algorithm.

# Keyword arguments

  * `maxiter::Int=256`: the number of maximum iterations.
  * `dist::SemiMetric=SqEuclidean()`: the distance function.
  * `ϵ::AbstractFloat=1.0e-6`: the absolute tolerance for convergence.
