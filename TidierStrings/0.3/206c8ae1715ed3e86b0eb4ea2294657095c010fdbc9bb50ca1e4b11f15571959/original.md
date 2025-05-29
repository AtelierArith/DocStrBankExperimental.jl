```
str_replace_missing(string::AbstractVector{Union{Missing,String}}, replacement::String="missing")
```

Replaces missing values in a vector with a specified string.

Arguments

  * `string`: Input vector of strings.
  * `replacement`: The string to replace missing values with. Default is "missing".

Returns The vector of strings with missing values replaced.

Examples

```jldoctest
julia> str_replace_missing(["apple", missing, "pear", "pineapple"])
4-element Vector{String}:
 "apple"
 "missing"
 "pear"
 "pineapple"
```
