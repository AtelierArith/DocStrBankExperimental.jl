```
str_flatten_comma(string::AbstractVector, last::Union{Nothing,AbstractString}=nothing; missing_rm::Bool=false)
```

文字列ベクトルをカンマで区切られた単一の文字列にフラット化します。

引数

  * `string`: 入力文字列。
  * `last`: フラット化された文字列の末尾に挿入する文字列。デフォルトは `nothing` です。
  * `missing_rm`: 入力ベクトルから `Missing` 値を削除します。デフォルトは `false` です。

返り値 フラット化された文字列。

例

```jldoctest
julia> str_flatten_comma(['a', 'b', 'c'])
"a, b, c"

julia> str_flatten_comma(['a', 'b'])
"a, b"

julia> str_flatten_comma(['a', 'b'], " and ")
"a and b"
```
