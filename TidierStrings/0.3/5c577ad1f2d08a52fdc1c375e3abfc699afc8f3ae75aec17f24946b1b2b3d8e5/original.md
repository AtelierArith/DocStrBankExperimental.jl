```
str_length(s::AbstractString)
```

Return the length of the string `s`.

Arguments

  * `s`: Input string.

Returns The length of the string `s`.

Examples

```jldoctest
julia> str_length("hello world! 😊")
14

julia> str_length("😊")
1
```
