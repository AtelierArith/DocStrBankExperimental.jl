```julia
by(ft, splitkeys)

```

列 `splitkeys` によってテーブルの行をグループ化するイテレータで、インデックスキーの各連続ブロックに対して `(index::NamedTuple, table::FunctionalTable)` を返します。

この関数には便利な形式 `by(ft, splitkeys...; ...)` があります。
