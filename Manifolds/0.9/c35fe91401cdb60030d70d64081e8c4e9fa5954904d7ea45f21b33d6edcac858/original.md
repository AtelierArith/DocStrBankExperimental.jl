```
Random.rand(G::GeneralLinear; vector_at=nothing, kwargs...)
```

If `vector_at` is `nothing`, return a random point on the [`GeneralLinear`](@ref) group `G` by using `rand` in the embedding.

If `vector_at` is not `nothing`, return a random tangent vector from the tangent space of the point `vector_at` on the [`GeneralLinear`](@ref) by using by using `rand` in the embedding.
