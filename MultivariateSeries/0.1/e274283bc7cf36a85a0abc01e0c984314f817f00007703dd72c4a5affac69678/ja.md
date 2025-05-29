```
moment(w::Vector{C}, P::Matrix{C}) -> Vector{Int64} -> C
```

次の点の次元 n の r 点の列 P に関連するモーメント関数 $α -> ∑_{i} ω_{i} P_{i}^α$ を計算します。これはサイズ r*n の行列であり、重み w を持ちます。
