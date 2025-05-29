```
str_count(string::String, pattern::Union{String, Regex})
```

Count the number of non-overlapping occurrences of a pattern in a string.

# Arguments

  * `string`: The string in which to count the pattern.
  * `pattern`: A string or a regular expression to find within the string.

The pattern can include special logic:

Use | to represent "or" (e.g., "red|blue" counts any string that contains "red" or "blue"). Returns The count of non-overlapping occurrences of pattern in string. Examples

```jldoctest
julia> str_count("The blue sky is blue", "blue")
2

julia> str_count("The blue sky is blue", r"blu")
2

julia> str_count("The blue sky is blue", "blue|sky")
3
```
