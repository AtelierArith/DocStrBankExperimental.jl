```
==(a::AbstractString, b::AbstractString) -> Bool
```

Test whether two strings are equal character by character (technically, Unicode code point by code point).

# Examples

```jldoctest
julia> "abc" == "abc"
true

julia> "abc" == "αβγ"
false
```
