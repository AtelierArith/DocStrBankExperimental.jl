```
str_remove_all(string::String, pattern::Union{String, Regex})
```

Remove all occurrences of the pattern in the string.

# Arguments

  * `string`: The string from which the pattern should be removed.
  * `pattern`: The pattern which should be removed from the string. Can be a string or a regular expression.

Returns A string with all occurrences of the pattern removed.

Examples

```jldoctest
julia> string = "I love tidier strings, I love tidier strings"
"I love tidier strings, I love tidier strings"

julia> str_remove_all(string, " strings")
"I love tidier , I love tidier "
```
