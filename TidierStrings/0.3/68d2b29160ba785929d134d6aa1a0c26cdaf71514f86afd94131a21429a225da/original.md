```
str_flatten(string::AbstractVector, collapse::AbstractString="", last::Union{Nothing,AbstractString}=nothing; missing_rm::Bool=false)
```

Flatten a string vector into a single string.

Arguments

  * `string`: Input string.
  * `collapse`: The string to insert between each string in the input vector. Default is `""`.
  * `last`: The string to insert at the end of the flattened string. Default is `nothing`.
  * `missing_rm`: Remove `Missing` values from the input vector. Default is `false`.

Returns A flattened string.

Examples

```jldoctest
julia> str_flatten(["a", "b", "c"])
"abc"

julia> str_flatten(["a", "b", "c", "d"])
"abcd"

julia> str_flatten(['a', 'b', 'c'], "-")
"a-b-c"

julia> str_flatten(['a', 'b', 'c'], ", ")
"a, b, c"

julia> str_flatten(['a', 'b', 'c'], ", ", " and ")
"a, b and c"
```
