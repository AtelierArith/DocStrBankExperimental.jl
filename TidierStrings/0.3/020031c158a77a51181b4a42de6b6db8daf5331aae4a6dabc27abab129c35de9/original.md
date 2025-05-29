```
str_unique(strings::AbstractVector{<:AbstractString}; ignore_case::Bool=false)
```

Remove duplicates from a vector of strings.

Arguments

  * `strings`: Input vector of strings.
  * `ignore_case`: Whether to ignore case when comparing strings. Default is `false`.

Returns A vector of unique strings from the input vector.

Examples

```jldoctest
julia> str_unique(["apple", "banana", "pear", "banana", "Apple"])
4-element Vector{String}:
 "apple"
 "banana"
 "pear"
 "Apple"
```
