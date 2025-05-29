```
is_subset(H::GAPGroup, G::GAPGroup)
```

Return `true` if `H` is a subset of `G`, otherwise return `false`.

# Examples

```jldoctest
julia> g = symmetric_group(300); h = derived_subgroup(g)[1];

julia> is_subset(h, g)
true

julia> is_subset(g, h)
false
```
