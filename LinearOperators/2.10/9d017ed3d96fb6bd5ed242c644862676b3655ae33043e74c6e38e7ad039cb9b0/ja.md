```
opEye(T, nrow, ncol; S = Vector{T})
opEye(nrow, ncol)
```

サイズ `nrow`x`ncol` の矩形単位演算子で、データ型は `T`（デフォルトは `Float64`）。`S` を使用して GPU 上の LinearOperators に変更します。
