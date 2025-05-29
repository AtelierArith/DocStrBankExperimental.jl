```
str_locate_all(string::AbstractString, pattern::Union{AbstractString, Regex})
```

Returns the indices of all occurrences of a pattern in a string.

Arguments

  * `string`: Input string.
  * `pattern`: The pattern to search for. Can be a string or a regular expression.

A vector of tuples `(start, end)` where `start` is the position at the start of the match and `end` is the position of the end.

Examples

```jldoctest
julia> fruit = ["apple", "banana", "pear", "pineapple"]; str_locate_all(fruit[1], "e")
1-element Vector{Tuple{Int64, Int64}}:
 (5, 5)

julia> fruit = ["apple", "banana", "pear", "pineapple"]; str_locate_all(fruit[2], "a")
3-element Vector{Tuple{Int64, Int64}}:
 (2, 2)
 (4, 4)
 (6, 6)
```
