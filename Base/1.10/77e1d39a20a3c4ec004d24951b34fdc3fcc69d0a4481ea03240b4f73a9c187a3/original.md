```
startswith(s::AbstractString, prefix::AbstractString)
```

Return `true` if `s` starts with `prefix`. If `prefix` is a vector or set of characters, test whether the first character of `s` belongs to that set.

See also [`endswith`](@ref), [`contains`](@ref).

# Examples

```jldoctest
julia> startswith("JuliaLang", "Julia")
true
```
