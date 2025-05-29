```
str_locate(string::AbstractString, pattern::Union{AbstractString, Regex})
```

Returns the index of the first occurrence of a pattern in a string.

Arguments

  * `string`: Input string.
  * `pattern`: The pattern to search for. Can be a string or a regular expression.

A tuple `(start, end)` where `start` is the position at the start of the match and `end` is the position of the end.

Examples

```jldoctest
julia> fruit = ["apple", "banana", "pear", "pineapple"]; str_locate(fruit[1], "e")
(5, 5)

julia> fruit = ["apple", "banana", "pear", "pineapple"]; str_locate(fruit[2], "a")
(2, 2)
```
