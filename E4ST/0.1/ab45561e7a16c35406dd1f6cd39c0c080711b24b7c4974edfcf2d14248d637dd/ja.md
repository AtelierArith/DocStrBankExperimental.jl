```
get_table_row_idxs(data, table_name, conditions...) -> row_idxs::Vector{Int64}
```

`conditions`が真である`data[table_name]`の行インデックスを取得します。可能な条件の説明については[`get_table`](@ref)を参照してください。
