```
as_integer(value)
```

数値または文字列を Int64 データ型に変換します。

これは型変換のための便利なヘルパーです。欠損値は伝播されます。小数点以下の値は削除されます。

# 引数

  * `value`: `AbstractString`、`Number`、または `missing` 値。

# 例

```jldoctest
julia> as_integer(1)
1

julia> as_integer(1.5)
1

julia> as_integer("2")
2

julia> as_integer("2.5")
2

julia> as_integer(missing)
missing
```
