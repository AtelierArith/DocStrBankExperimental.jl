```
inv_right_compose(G::AbstractLieGroup, h, g)
inv_right_compose!(G::AbstractLieGroup, k, h, g)
```

Compute the inverse of the right group operation $ρ_g(h) = h∘g$, on the [`AbstractLieGroup`](@ref) `G`, that is compute $ρ_g^{-1}(h) = h∘g^{-1}$. This can be done in-place of `k`.
