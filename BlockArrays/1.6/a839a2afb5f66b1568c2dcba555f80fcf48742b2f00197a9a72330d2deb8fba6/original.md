```
blockisequal(a::AbstractUnitRange{<:Integer}, b::AbstractUnitRange{<:Integer})
```

Check if `a` and `b` have the same block structure.

# Examples

```jldoctest
julia> b1 = blockedrange([1,2])
2-blocked 3-element BlockedOneTo{Int64, Vector{Int64}}:
 1
 ─
 2
 3

julia> b2 = blockedrange([1,1,1])
3-blocked 3-element BlockedOneTo{Int64, Vector{Int64}}:
 1
 ─
 2
 ─
 3

julia> blockisequal(b1, b1)
true

julia> blockisequal(b1, b2)
false
```
