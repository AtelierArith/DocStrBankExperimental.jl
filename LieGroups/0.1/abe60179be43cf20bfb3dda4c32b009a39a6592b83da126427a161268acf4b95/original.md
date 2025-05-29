```
inv_left_compose(G::AbstractLieGroup, g, h)
inv_left_compose!(G::AbstractLieGroup, k, g, h)
```

Compute the inverse of the left group operation $λ_g(h) = g∘h$, on the [`AbstractLieGroup`](@ref) `G`, that is, compute $λ_g^{-1}(h) = g^{-1}∘h$. This can be done in-place of `k`.
