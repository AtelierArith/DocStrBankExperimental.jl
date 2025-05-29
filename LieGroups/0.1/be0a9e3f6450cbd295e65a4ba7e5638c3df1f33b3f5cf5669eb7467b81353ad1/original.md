```
diff_conjugate(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, g, h, X)
diff_conjugate!(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, Y, g, h, X)
```

Compute the differential of the conjugate $c_g(h) = g∘h∘g^{-1} = ghg^{-1}$, which simplifies for an [`AbelianMultiplicationGroupOperation`](@ref) to $D(c_g(h))[X] = X$.

This can be computed in-place of `Y` if `Y` is `mutable`.
