```
str_replace_missing(string::AbstractVector{Union{Missing,String}}, replacement::String="missing")
```

指定された文字列でベクター内の欠損値を置き換えます。

引数

  * `string`: 文字列の入力ベクター。
  * `replacement`: 欠損値を置き換えるための文字列。デフォルトは "missing"。

返り値 欠損値が置き換えられた文字列のベクター。

例

```jldoctest
julia> str_replace_missing(["apple", missing, "pear", "pineapple"])
4-element Vector{String}:
 "apple"
 "missing"
 "pear"
 "pineapple"
```
