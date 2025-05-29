```
str_pad(string::AbstractString, width::Integer; side::String="right", pad::AbstractString=" ", use_width::Bool=true)
```

文字列を特定の幅にパディングします。

# 戻り値

パディングされた文字列。

# 引数

  * `string`: パディングする文字列。
  * `width`: 文字列をパディングする幅。
  * `side`: 文字列をパディングする側。 "left"、"right"、または "both" のいずれか。
  * `pad`: パディングに使用する文字列。
  * `use_width`: 幅の引数を使用するか、文字列の長さを使用するか。

# 例

```jldoctest
julia> str_pad("hello", 10)
"hello     "

julia> str_pad("hello", 10, side="left")
"     hello"

julia> str_pad("hello", 10, side="both")
"  hello   "

julia> str_pad("hello", 10, side="both", pad="*")
"**hello***"
```
