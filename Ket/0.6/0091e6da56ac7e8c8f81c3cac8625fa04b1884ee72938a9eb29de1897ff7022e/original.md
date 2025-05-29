```
orthonormal_range(A::AbstractMatrix{T}; tol::T=nothing) where {T<:Number}
```

Orthonormal basis for the range of `A`. When `A` is sparse and `T` ∈ [`Float64`, `ComplexF64`, `Float32`, `ComplexF32`], uses a QR factorization and returns a sparse result, otherwise uses an SVD and returns a dense matrix. Tolerance `tol` is used to compute the rank and is automatically set if not provided.
