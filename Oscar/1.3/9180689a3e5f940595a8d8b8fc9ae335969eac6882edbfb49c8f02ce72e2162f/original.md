```
SubPcGroupElem
```

Element of a subgroup of a polycyclic group.

The elements are displayed in the same way as the elements of full polycyclic groups, see [`PcGroupElem`](@ref).

# Examples

```jldoctest
julia> G = abelian_group(SubPcGroup, [4, 2]);

julia> G[1], G[2]
(f1, f3)

julia> G[2]*G[1]
f1*f3
```
