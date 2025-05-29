```
pairwise!(r::AbstractMatrix, dist::PreMetric, a::AbstractMatrix, b::AbstractMatrix; dims)
```

Same as `pairwise!(dist, r, a, b; dims)`.

!!! warning
    Since this alternative syntax is deprecated and will be removed in a future release of Distances.jl, its use is discouraged. Please call `pairwise!(dist, r, a, b; dims)` instead.

