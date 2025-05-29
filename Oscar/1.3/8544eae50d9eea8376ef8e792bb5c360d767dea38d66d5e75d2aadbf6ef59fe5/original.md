```
is_finite(G::GAPGroup) -> Bool
```

Return `true` if `G` is finite, and `false` otherwise.

# Examples

```jldoctest
julia> is_finite(symmetric_group(5))
true

julia> is_finite(free_group(2))
false

```
