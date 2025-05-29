```
blockedrange(blocklengths::Union{Tuple, AbstractVector})
blockedrange(first::Integer, blocklengths::Union{Tuple, AbstractVector})
```

Return a blocked `AbstractUnitRange{<:Integer}` with the block sizes being `blocklengths`. If `first` is provided, this is used as the first value of the range. Otherwise, if only the block lengths are provided, `first` is assumed to be `1`.

# Examples

```jldoctest
julia> blockedrange([1,2])
2-blocked 3-element BlockedOneTo{Int64, Vector{Int64}}:
 1
 ─
 2
 3

julia> blockedrange(2, (1,2))
2-blocked 3-element BlockedUnitRange{Int64, Tuple{Int64, Int64}}:
 2
 ─
 3
 4
```
