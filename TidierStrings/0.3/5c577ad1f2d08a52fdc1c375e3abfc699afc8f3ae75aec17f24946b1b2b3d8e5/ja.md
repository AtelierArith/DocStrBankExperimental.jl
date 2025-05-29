```
str_length(s::AbstractString)
```

文字列 `s` の長さを返します。

引数

  * `s`: 入力文字列。

返り値 `s` の文字列の長さ。

例

```jldoctest
julia> str_length("hello world! 😊")
14

julia> str_length("😊")
1
```
