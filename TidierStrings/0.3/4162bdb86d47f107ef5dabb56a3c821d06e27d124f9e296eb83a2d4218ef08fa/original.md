```
str_subset(string::String, pattern::Union{String, Regex})
```

Subset a string based on the presence of pattern. If the pattern exists within the string, the function will return the original string. If the pattern is not found within the string, the function will return an empty string.

# Arguments

  * `string`: The string from which to extract the subset.
  * `pattern`: The pattern to search for within the string. Can be a plain string or a Regex.

Returns The original string if the pattern is found within it, otherwise an empty string.

# Examples

```jldoctest
julia> str_subset("Hello world!", "world")
"Hello world!"

julia> str_subset("Hello world!", "universe")
""
```
