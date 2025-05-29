```
as_string(value)
```

数値または文字列をStringデータ型に変換します。

これは型変換のための便利なヘルパーです。欠損値は伝播します。

# 引数

  * `value`: `AbstractString`、`Number`、または`missing`値。

# 例

```jldoctest
julia> as_string(1)
"1"

julia> as_string(1.5)
"1.5"

julia> as_string(missing)
missing
```
