```
str_remove(string::String, pattern::Union{String, Regex})
```

Remove the first occurrence of the pattern in the string.

Arguments

  * `string`: The string from which the pattern should be removed.
  * `pattern`: The pattern which should be removed from the string. Can be a string or a regular expression.

Returns A string with the first occurrence of the pattern removed.

Examples

```jldoctest
julia> string = "I love tidier strings strings"
"I love tidier strings strings"

julia> str_remove(string, " strings")
"I love tidier strings"
```
