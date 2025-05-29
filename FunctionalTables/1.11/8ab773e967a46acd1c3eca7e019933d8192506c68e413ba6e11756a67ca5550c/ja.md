```julia
struct FunctionalTable{C<:NamedTuple, O<:Tuple{Vararg{FunctionalTables.ColumnOrdering}}}
```

# 内部ノート

  * アクセサ `length`、`colums`、および `ordering` を使用してフィールドにアクセスします。プロパティアクセサは `columns` に転送されます。
  * 内部コンストラクタは、長さと順序が信頼されている（したがってチェックされていない）ものだけです。外部コンストラクタは、最初に順序ルールをラップし、その後に長さを計算/検証する必要があります。
