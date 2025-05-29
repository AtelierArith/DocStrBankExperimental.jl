```
BlockedOneTo{T, <:Union{AbstractVector{T}, NTuple{<:Any,T}}} where {T}
```

Define an `AbstractUnitRange{T}` that has been divided into blocks, which is used to represent `axes` of block arrays. This parallels `Base.OneTo` in that the first value is guaranteed to be `1`.

Construction is typically via `blockedrange` which converts a vector of block lengths to a `BlockedUnitRange`.

# Examples

```jldoctest
julia> blockedrange([2,2,3]) # block lengths
3-blocked 7-element BlockedOneTo{Int64, Vector{Int64}}:
 1
 2
 ─
 3
 4
 ─
 5
 6
 7
```

See also [`BlockedUnitRange`](@ref).
