```
vtmanhattan(x::AbstractArray, y::AbstractArray; dims=:)
```

Compute the Manhattan distance between the vectors corresponding to the slices along the dimensions `dims`. Threaded.

See also: [`vteuclidean`](@ref), [`vtchebyshev`](@ref), [`vtminkowski`](@ref)
