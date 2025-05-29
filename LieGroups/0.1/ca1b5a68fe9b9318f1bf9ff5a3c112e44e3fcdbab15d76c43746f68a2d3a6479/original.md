```
cross(G::LieGroup, H::LieGroup)
G × H
G1 × G2 × G3 × ...
```

Return the [`ProductLieGroup`](@ref) For two [`LieGroups`](@ref) `G` and `H`, where for the case that one of them is a [`ProductLieGroup`](@ref) itself, the other is either prepended (if `H` is a product) or appended (if `G` is). If both are product Lie groups, they are combined into one, keeping the order of operations.

For the case that more than two are concatenated with `×` this is iterated.
