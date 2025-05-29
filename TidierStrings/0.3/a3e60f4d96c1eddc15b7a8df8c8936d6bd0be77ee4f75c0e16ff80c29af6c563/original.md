```
str_width(s::AbstractString)
```

Return the width of the string `s`.

Arguments

  * `s`: Input string.

Returns The width of the string `s`.

Examples

```jldoctest
julia> str_width("hello world! 😊")
15

julia> str_width("😊")
2
```
