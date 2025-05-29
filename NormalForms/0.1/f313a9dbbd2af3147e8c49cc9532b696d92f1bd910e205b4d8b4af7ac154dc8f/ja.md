```
hnfr!(M::AbstractMatrix{<:Integer}, R::RoundingMode = NegativeOffDiagonal)
    -> RowHermite{eltype(M),typeof(M)}
```

整数行列 `M` の行ヘルミート正規形をインプレースで計算し、因子分解の要素を記述する `RowHermite` を返します。
