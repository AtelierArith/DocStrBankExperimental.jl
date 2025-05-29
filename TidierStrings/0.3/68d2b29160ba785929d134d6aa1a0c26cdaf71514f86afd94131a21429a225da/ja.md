```
str_flatten(string::AbstractVector, collapse::AbstractString="", last::Union{Nothing,AbstractString}=nothing; missing_rm::Bool=false)
```

文字列ベクトルを単一の文字列にフラット化します。

引数

  * `string`: 入力文字列。
  * `collapse`: 入力ベクトル内の各文字列の間に挿入する文字列。デフォルトは `""`。
  * `last`: フラット化された文字列の末尾に挿入する文字列。デフォルトは `nothing`。
  * `missing_rm`: 入力ベクトルから `Missing` 値を削除します。デフォルトは `false`。

返り値 フラット化された文字列。

例

```jldoctest
julia> str_flatten(["a", "b", "c"])
"abc"

julia> str_flatten(["a", "b", "c", "d"])
"abcd"

julia> str_flatten(['a', 'b', 'c'], "-")
"a-b-c"

julia> str_flatten(['a', 'b', 'c'], ", ")
"a, b, c"

julia> str_flatten(['a', 'b', 'c'], ", ", " and ")
"a, b and c"
```
