```
vtminkowski(x::AbstractArray, y::AbstractArray, p::Real; dims=:)
```

Compute the Minkowski distance between the vectors corresponding to the slices along the dimensions `dims`. Threaded.

`p` can assume any numeric value (even though not all values produce a mathematically valid vector norm). `vtminkowski(x, y, Inf)` returns the largest value in `abs.(x .- y)`, whereas `vtminkowski(x, y, -Inf)` returns the smallest.

See also: [`vtmanhattan`](@ref), [`vteuclidean`](@ref), [`vtchebyshev`](@ref)
