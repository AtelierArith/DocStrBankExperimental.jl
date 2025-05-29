```
blocklasts(a::AbstractUnitRange{<:Integer})
```

Return the last index of each block of `a`.

# Examples

```jldoctest
julia> b = blockedrange([1,2,3])
3-blocked 6-element BlockedOneTo{Int64, Vector{Int64}}:
 1
 ─
 2
 3
 ─
 4
 5
 6

julia> blocklasts(b)
3-element Vector{Int64}:
 1
 3
 6
```
