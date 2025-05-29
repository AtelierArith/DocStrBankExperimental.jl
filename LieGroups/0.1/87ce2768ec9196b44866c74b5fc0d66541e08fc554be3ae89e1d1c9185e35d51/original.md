```
diff_inv(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, g, X)
diff_inv!(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, Y, g, X)
```

Compute the value of the differential $Dι_{\mathcal G}(g)[X]$ of the inversion $ι_{\mathcal G}(g) := g^{-1}$ at $X ∈ 𝔤$ in the [`LieAlgebra`](@ref) $𝔤$ of the [`LieGroup`](@ref) `G`.

In the abelian case, the computation simplifies to

$$
Dι_{\mathcal G}(g)[X] = -gXg^{-1} = -X.
$$

This can be computed in-place of `Y` if `Y` is `mutable`.
