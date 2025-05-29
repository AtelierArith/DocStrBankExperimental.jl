```
Collar(table; [holeid], [x], [y], [z])
```

コラール `table` は、指定された `holeid` を持つドリルホールの頭の `x`、`y`、`z` 座標（通常はメートル単位）を格納します。

キーワード引数が省略された場合、`table` で一般的な列名が検索されます。

## 例

```julia
Collar(table, holeid="BHID", x="EASTING", y="NORTHING")
Collar(table, x="XCOLLAR", y="YCOLLAR", z="ZCOLLAR")
```

関連情報は [`Survey`](@ref)、[`Interval`](@ref) を参照してください。
