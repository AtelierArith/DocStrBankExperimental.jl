```
BlockedUnitRange
```

is an `AbstractUnitRange{<:Integer}` that has been divided into blocks. Construction is typically via `blockedrange` which converts a vector of block lengths to a `BlockedUnitRange`.

# Examples

```jldoctest
julia> blockedrange(2, [2,2,3]) # first value and block lengths
3-blocked 7-element BlockedUnitRange{Int64, Vector{Int64}}:
 2
 3
 ─
 4
 5
 ─
 6
 7
 8
```

See also [`BlockedOneTo`](@ref).
