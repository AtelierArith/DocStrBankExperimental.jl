```
inv(G::AbstractLieGroup, g)
inv!(G::AbstractLieGroup, h, g)
```

Compute the inverse group element $g^{-1}$ with respect to the [`AbstractGroupOperation`](@ref) $∘$ on the [`AbstractLieGroup`](@ref) $\mathcal G$, that is, return the unique element $h=g^{-1}$ such that $h∘g=\mathrm{e}$, where $\mathrm{e}$ denotes the [`Identity`](@ref).

This can be done in-place of `h`, without side effects, that is you can do `inv!(G, g, g)`.
