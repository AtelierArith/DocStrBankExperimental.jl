```
diff_left_compose(G::AbstractLieGroup, g, h, X)
diff_left_compose!(G::AbstractLieGroup, Y, g, h, X)
```

Compute the differential of the left group multiplication $λ_g(h) = g∘h$, on the [`AbstractLieGroup`](@ref) `G`, that is Compute $Dλ_g(h)[X]$, $X ∈ 𝔤$. This can be done in-place of `Y`.
