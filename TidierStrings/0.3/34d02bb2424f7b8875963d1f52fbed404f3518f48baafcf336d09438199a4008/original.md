```
str_flatten_comma(string::AbstractVector, last::Union{Nothing,AbstractString}=nothing; missing_rm::Bool=false)
```

Flatten a string vector into a single string, separated by commas.

Arguments

  * `string`: Input string.
  * `last`: The string to insert at the end of the flattened string. Default is `nothing`.
  * `missing_rm`: Remove `Missing` values from the input vector. Default is `false`.

Returns A flattened string.

Examples

```jldoctest
julia> str_flatten_comma(['a', 'b', 'c'])
"a, b, c"

julia> str_flatten_comma(['a', 'b'])
"a, b"

julia> str_flatten_comma(['a', 'b'], " and ")
"a and b"
```
