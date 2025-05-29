```
str_starts(string::String, pattern::Union{AbstractString, Regex}; negate::Bool=false)
```

Check if a string starts with a certain pattern.

Arguments

  * `string`: Input string.
  * `pattern`: The pattern to check for. Can be a string or a regular expression.
  * `negate`: Whether to negate the result. Default is `false`.

Returns A vector of booleans indicating if the string starts with the pattern.

Examples

```jldoctest
julia> str_starts.(["apple", "banana", "pear", "pineapple"], r"^p")  # [false, false, true, true]
4-element BitVector:
 0
 0
 1
 1
julia> str_starts.(["apple", "banana", "pear", "pineapple"], r"^p", negate=true)  # [true, true, false, false]
4-element BitVector:
 1
 1
 0
 0
julia> str_starts("apple pineapple", r"^p")
false
```
