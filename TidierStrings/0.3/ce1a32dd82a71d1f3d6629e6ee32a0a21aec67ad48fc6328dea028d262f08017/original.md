```
str_squish(string::String)
```

Squish a string, removing consecutive whitespace and replacing it with a single space, as well as removing leading and trailing whitespace.

#Arguments `string`: The string to be squished. Returns A squished version of string.

# Examples

```jldoctest
julia> str_squish("  This    is a string   with   spaces   ")
"This is a string with spaces"

julia> str_squish("  Leading and trailing spaces   ")
"Leading and trailing spaces"
```
