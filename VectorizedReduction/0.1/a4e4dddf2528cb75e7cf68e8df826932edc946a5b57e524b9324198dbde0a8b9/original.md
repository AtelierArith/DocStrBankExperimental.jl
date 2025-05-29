```
vminkowski(x::AbstractArray, y::AbstractArray, p::Real; dims=:)
```

Compute the Minkowski distance between the vectors corresponding to the slices along the dimensions `dims`.

`p` can assume any numeric value (even though not all values produce a mathematically valid vector norm). `vminkowski(x, y, Inf)` returns the largest value in `abs.(x .- y)`, whereas `vminkowski(x, y, -Inf)` returns the smallest.

See also: [`vmanhattan`](@ref), [`veuclidean`](@ref), [`vchebyshev`](@ref)
