```
LinearAlgebra.mul!(out, st::Union{Transpose{T, SnpLinAlg{T}}, Adjoint{T, SnpLinAlg{T}}}, V)
```

In-place matrix-matrix multiplication, with transposed `SnpLinAlg`.
