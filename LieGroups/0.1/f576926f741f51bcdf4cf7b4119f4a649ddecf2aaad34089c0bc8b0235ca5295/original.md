```
diff_inv(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, g, X)
diff_inv!(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, Y, g, X)
```

Compute the value of differential $Dι_{\mathcal G}(g)[X]$ of matrix inversion $ι_{\mathcal G}(g) := g^{-1}$ at $X ∈ 𝔤$ in the [`LieAlgebra`](@ref) $𝔤$ of the [`LieGroup`](@ref) `G`.

The formula is given by

$$
Dι_{\mathcal G}(g)[X] = -g^{\mathrm{T}}Xg^{-1},
$$

which stems from using the differential of the inverse from [Giles:2008](@cite) given by $D(g^{-1})[X] = -g^{-1}Xg^{-1}$ composed with the push forward of the left composition $Dλ_\mathrm{e}(g)[X] = gX$ mapping from the Liea algebra into the tangent space at $g$, and its adjoint $D^*λ_\mathrm{e}(g)[X] = g^{\mathrm{T}}X$. Then we get $g^{\mathrm{T}}(g^{-1}(gX)g^{-1})$ which simplifies to $-g^{\mathrm{T}}Xg^{-1}$ from above.
