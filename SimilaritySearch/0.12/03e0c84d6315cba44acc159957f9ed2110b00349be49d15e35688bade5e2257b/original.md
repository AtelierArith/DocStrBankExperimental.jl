```
struct StrideMatrixDatabase{M<:StrideArray} <: AbstractDatabase

StrideMatrixDatabase(matrix::StrideArray)
```

Wraps a matrix object into a `StrideArray` and wrap it as a database. Please see [`AbstractDatabase`](@ref) for general usage.
