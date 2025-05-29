```
diff_conjugate(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, g, h, X)
diff_conjugate!(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, Y, g, h, X)
```

Compute the differential of the conjugate $c_g(h) = g∘h∘g^{-1} = ghg^{-1}$, which simplifies for an [`AbstractMultiplicationGroupOperation`](@ref) to $D(c_g(h))[X] = gXg^{-1}$.
