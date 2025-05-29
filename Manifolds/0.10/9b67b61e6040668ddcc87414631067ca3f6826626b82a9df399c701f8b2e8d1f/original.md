```
Random.rand(M::DeterminantOneMatrices; vector_at=nothing, kwargs...)
```

If `vector_at` is `nothing`, return a random point on the [`DeterminantOneMatrices`](@ref) manifold `M` by using `rand` in the embedding.

If `vector_at` is not `nothing`, return a random tangent vector from the tangent space of the point `vector_at` on the [`DeterminantOneMatrices`](@ref) by using by using `rand` in the embedding.
