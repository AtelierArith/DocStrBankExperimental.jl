```
initseeds(alg::Union{SeedingAlgorithm, Symbol},
          X::AbstractMatrix, k::Integer) -> Vector{Int}
```

Select `k` seeds from a $d×n$ data matrix `X` using the `alg` algorithm.

`alg` could be either an instance of [`SeedingAlgorithm`](@ref) or a symbolic name of the algorithm.

Returns the vector of `k` seed indices.
