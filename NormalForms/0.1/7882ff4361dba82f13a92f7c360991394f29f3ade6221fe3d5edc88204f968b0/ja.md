```
hnfc(M::AbstractMatrix{T<:Integer}) -> ColumnHermite{T,typeof(M)}
    -> ColumnHermite{eltype(M),typeof(M)}
```

整数行列 `M` の列ヘルミート正規形をインプレースで計算し、因子分解の要素を記述する `ColumnHermite` を返します。`hnfc!()` とは異なり、この関数は入力行列のコピーを作成し、インプレースで変更することはありません。
