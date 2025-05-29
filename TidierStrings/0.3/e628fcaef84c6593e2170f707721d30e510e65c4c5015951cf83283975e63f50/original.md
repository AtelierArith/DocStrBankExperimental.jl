```
str_ends(string::String, pattern::Union{AbstractString, Regex}; negate::Bool=false)
```

Check if a string ends with a certain pattern.

Arguments

  * `string`: Input string.
  * `pattern`: The pattern to check for. Can be a string or a regular expression.
  * `negate`: Whether to negate the result. Default is `false`.

Returns A vector of booleans indicating if the string ends with the pattern.

Examples

```jldoctest
julia> str_ends("apple pineapple", r"^p")
false

julia> str_ends.(["apple", "banana", "pear", "pineapple"], r"e$")  # [true, false, false, true]
4-element BitVector:
 1
 0
 0
 1
julia> str_ends.(["apple", "banana", "pear", "pineapple"], r"e$", negate=true)  # [false, true, true, false]
4-element BitVector:
 0
 1
 1
 0
```
