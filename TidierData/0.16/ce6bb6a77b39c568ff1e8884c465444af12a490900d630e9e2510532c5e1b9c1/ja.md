```
as_float(value)
```

数値または文字列を Float64 データ型に変換します。

これは型変換のための便利なヘルパーです。欠損値は伝播します。

# 引数

  * `value`: `AbstractString`、`Number`、または `missing` 値。

# 例

```jldoctest
julia> as_float(1)
1.0

julia> as_float("1.5")
1.5

julia> as_float(missing)
missing
```
