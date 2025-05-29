```
compose(G::AbstractLieGroup, g, h)
compose!(G::AbstractLieGroup, k, g, h)
```

Perform the group operation $g ∘ h$ for two $g, h ∈ \mathcal G$ on the [`AbstractLieGroup`](@ref) `G`. This can also be done in-place of `h`.

!!! info
    This function also handles the case where `g` or/and `h` are the [`Identity`](@ref)`(G)`. Since this would lead to ambiguities when implementing a new group operations, this function calls `_compose` and `_compose!`, respectively, which is meant for the actual computation of group operations on (non-[`Identity`](@ref)` but maybe its numerical representation) elements.

