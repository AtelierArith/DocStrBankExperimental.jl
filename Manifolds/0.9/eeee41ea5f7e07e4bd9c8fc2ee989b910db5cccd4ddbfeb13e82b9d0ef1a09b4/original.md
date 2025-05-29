```
rand(::KendallsShapeSpace; vector_at=nothing)
```

When `vector_at` is `nothing`, return a random point `x` on the [`KendallsShapeSpace`](@ref) manifold `M` by generating a random point in the embedding.

When `vector_at` is not `nothing`, return a random vector from the tangent space with mean zero and standard deviation `σ`.
