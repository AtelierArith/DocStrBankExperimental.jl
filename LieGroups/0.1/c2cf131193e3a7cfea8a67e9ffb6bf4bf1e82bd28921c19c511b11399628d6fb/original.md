```
diff_left_compose(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, g, h, X)
diff_left_compose!(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, Y, g, h, X)
```

Compute the differential of the left group multiplication $λ_g(h) = g∘h$, which simplifies for an [`AbstractMultiplicationGroupOperation`](@ref) to $Dλ_g(h)[X] = gX$.
