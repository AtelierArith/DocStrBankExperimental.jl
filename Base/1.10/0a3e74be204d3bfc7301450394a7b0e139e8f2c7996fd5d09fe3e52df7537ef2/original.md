```
endswith(s::AbstractString, suffix::AbstractString)
```

Return `true` if `s` ends with `suffix`. If `suffix` is a vector or set of characters, test whether the last character of `s` belongs to that set.

See also [`startswith`](@ref), [`contains`](@ref).

# Examples

```jldoctest
julia> endswith("Sunday", "day")
true
```
