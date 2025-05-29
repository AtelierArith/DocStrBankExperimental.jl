`FlexMatrix{T}(rows,cols)` は、`rows` でインデックス付けされた行、`cols` でインデックス付けされた列を持ち、すべてのエントリが型 `T` のゼロである新しい `FlexMatrix` を作成します（省略した場合は `Number` です）。

`FlexMatrix(v::FlexVector)` は、`v` を唯一の列インデックスが `Int(1)` の1列の `FlexMatrix` に変換します。
