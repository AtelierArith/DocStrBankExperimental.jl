```
struct MatrixDatabase{M<:AbstractDatabase} <: AbstractDatabase

MatrixDatabase(matrix::AbstractMatrix)
```

Wraps a matrix-like object `matrix` into a `MatrixDatabase`. Please see [`AbstractDatabase`](@ref) for general usage.
