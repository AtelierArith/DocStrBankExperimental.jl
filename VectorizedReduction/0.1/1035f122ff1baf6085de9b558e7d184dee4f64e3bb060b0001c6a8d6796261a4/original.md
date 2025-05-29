```
vtchebyshev(x::AbstractArray, y::AbstractArray; dims=:)
```

Compute the Chebyshev distance between the vectors corresponding to the slices along the dimensions `dims`. Threaded.

See also: [`vtmanhattan`](@ref), [`vteuclidean`](@ref), [`vtminkowski`](@ref)
