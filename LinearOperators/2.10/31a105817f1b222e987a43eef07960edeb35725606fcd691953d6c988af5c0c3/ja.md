```
opZeros(T, nrow, ncol; S = Vector{T})
opZeros(nrow, ncol)
```

サイズ `nrow` x `ncol` のゼロ演算子、データ型 `T`（デフォルトは `Float64`）。`S` を使用して GPU 上の LinearOperators に変更します。
