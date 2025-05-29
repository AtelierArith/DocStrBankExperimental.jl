```
str_dup(s::AbstractString, times::Int)
```

Duplicate the string `s` `times` times.

Arguments

  * `s`: Input string.
  * `times`: Number of times to duplicate the string.

Returns A string with the string `s` duplicated `times` times.

Examples

```jldoctest
julia> str_dup("hello", 3)
"hellohellohello"
```
