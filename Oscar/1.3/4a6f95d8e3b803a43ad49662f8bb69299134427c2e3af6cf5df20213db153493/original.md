```
PcGroupElem
```

Element of a polycyclic group.

The generators of a polycyclic group are displayed as `f1`, `f2`, `f3`, etc., and every element of a polycyclic group is displayed as product of the generators.

# Examples

```jldoctest
julia> G = abelian_group(PcGroup, [2, 3]);

julia> G[1], G[2]
(f1, f2)

julia> G[2]*G[1]
f1*f2
```

Note that this does not define Julia variables named `f1`, `f2`, etc.! To get the generators of the group `G`, use `gens(G)`; for convenience they can also be accessed as `G[1]`, `G[2]`, as shown in Section [Elements of groups](@ref elements_of_groups).
