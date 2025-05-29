```
TriMatrix{T}(layout::TriLayout, m::AbstractMatrix; diag=zero(T))
TriMatrix(layout::TriLayout, m::AbstractMatrix; [diag])
```

正方行列 `m` からデータをコピーして `TriMatrix` を作成します。

指定されていない場合、`T` は `eltype(m)` にデフォルト設定されます。
