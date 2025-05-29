```
vteuclidean(x::AbstractArray, y::AbstractArray; dims=:)
```

Compute the Euclidean distance between the vectors corresponding to the slices along the dimensions `dims`. Threaded.

See also: [`vtmanhattan`](@ref), [`vtchebyshev`](@ref), [`vtminkowski`](@ref)
