```
LinearAlgebra.mul!(out, st::Union{Transpose{T, SnpLinAlg{T}}, Adjoint{T, SnpLinAlg{T}}}, V)
```

転置された `SnpLinAlg` を用いたインプレース行列-行列乗算。
