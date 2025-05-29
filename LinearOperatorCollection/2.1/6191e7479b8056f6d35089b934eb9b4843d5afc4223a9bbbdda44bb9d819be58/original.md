```
normalOperator(prod::ProdOp{T, <:WeightingOp, matT}; kwargs...)
```

Fuses weights of `ẀeightingOp` by computing `adjoint.(weights) .* weights`
