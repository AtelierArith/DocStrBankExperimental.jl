```
opOnes(T, nrow, ncol; S = Vector{T})
opOnes(nrow, ncol)
```

データ型 `T` のサイズ `nrow`-by-`ncol` のすべての要素が1の演算子（デフォルトは `Float64`）。`S` を使用して GPU 上の LinearOperators に変更します。
