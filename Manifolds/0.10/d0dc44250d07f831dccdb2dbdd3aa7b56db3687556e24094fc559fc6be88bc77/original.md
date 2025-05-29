```
Random.rand(M::HeisenbergMatrices; vector_at = nothing, σ::Real=1.0)
```

If `vector_at` is `nothing`, return a random point on the [`HeisenbergMatrices`](@ref) `M` by sampling elements of the first row and the last column from the normal distribution with mean 0 and standard deviation `σ`.

If `vector_at` is not `nothing`, return a random tangent vector from the tangent space of the point `vector_at` on the [`HeisenbergMatrices`](@ref) by using a normal distribution with mean 0 and standard deviation `σ`.
