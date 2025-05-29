```
str_width(s::AbstractString)
```

文字列 `s` の幅を返します。

引数

  * `s`: 入力文字列。

返り値 文字列 `s` の幅。

例

```jldoctest
julia> str_width("hello world! 😊")
15

julia> str_width("😊")
2
```
