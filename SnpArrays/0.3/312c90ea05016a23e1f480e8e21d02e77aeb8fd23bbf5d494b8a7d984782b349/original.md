```
LinearAlgebra.mul!(out, st::Union{Transpose{T, SnpLinAlg{T}}, Adjoint{T, SnpLinAlg{T}}}, v)
```

In-place matrix-vector multiplication, with transposed `SnpLinAlg`.
