```
diff_right_compose(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, h, g, X)
diff_right_compose!(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, Y, h, g, X)
```

Compute the differential of the right group multiplication $ρ_g(h) = h∘g$, which simplifies for an [`AbstractMultiplicationGroupOperation`](@ref) to $Dρ_g(h)[X] = Xg$.
