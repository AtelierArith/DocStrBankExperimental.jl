```
hnfc!(M::AbstractMatrix{<:Integer}, R::RoundingMode = NegativeOffDiagonal)
    -> ColumnHermite{eltype(M),typeof(M)}
```

整数行列 `M` の列ヘルミート正規形をインプレースで計算し、因子分解の要素を記述する `ColumnHermite` を返します。
