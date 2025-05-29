```
adjustbags(b::AlignedBags, mask::AbstractVector{Bool})
```

Remove indices of instances brom bags `b` and remap the remaining instances accordingly.

# Examples

```jldoctest
julia> adjustbags(AlignedBags([1:2, 0:-1, 3:4]), [false, false, true, true])
AlignedBags{Int64}(UnitRange{Int64}[0:-1, 0:-1, 1:2])
```
