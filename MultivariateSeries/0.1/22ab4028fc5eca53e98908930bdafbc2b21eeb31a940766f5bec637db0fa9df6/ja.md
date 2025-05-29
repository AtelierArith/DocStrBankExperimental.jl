```
series(w::AbstractVector, P::AbstractMatrix, X, d::Int64) -> Series{C,M}
```

モーメント列の系列 $∑_i ω_{i} P_{i}^α$ を $|α| \leq d$ の場合に計算します。
