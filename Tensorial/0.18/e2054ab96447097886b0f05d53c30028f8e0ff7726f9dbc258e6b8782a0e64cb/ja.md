```
tomandel(A::Union{SymmetricSecondOrderTensor, SymmetricFourthOrderTensor})
```

テンソルをマンデル形式に変換します。これは `tovoigt(A, offdiagscale = √2)` に相当します。

詳細は [`tovoigt`](@ref) を参照してください。
