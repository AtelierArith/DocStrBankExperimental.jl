```
normalOperator(prod::ProdOp{T, <:WeightingOp, matT}; kwargs...)
```

`ẀeightingOp`の重みを`adjoint.(weights) .* weights`を計算することで融合します。
