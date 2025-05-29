```
str_which(string::Vector{T}, pattern::Union{AbstractString, Regex}; negate::Bool=false)
```

Returns the indices of strings where there's at least one match to the pattern.

# Arguments

  * `string`: Input string.
  * `pattern`: The pattern to check for. Can be a string or a regular expression.
  * `negate`: Whether to negate the result. Default is `false`.

# Returns

An integer vector containing indices of matching strings.

# Examples

```jldoctest
julia> str_which(["apple", "banana", "pear", "pineapple"], r"a")  # [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4
julia> str_which(["apple", "banana", "pear", "pineapple"], r"a", negate=true)  # []
Int64[]
julia> str_which(["apple", "banana", "pear", "pineapple"], "a", negate=true)  # []
Int64[]
```
