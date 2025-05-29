```
diff_right_compose(G::AbstractLieGroup, h, g, X)
diff_right_compose!(G::AbstractLieGroup, Y, h, g, X)
```

Compute the differential of the right group multiplication $ρ_g(h) = h∘g$, on the [`AbstractLieGroup`](@ref) `G`, that is Compute $Dρ_g(h)[X]$, $X ∈ 𝔤$ This can be done in-place of `Y`.
