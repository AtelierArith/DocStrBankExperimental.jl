```
inner(M::MetricManifold{ℝ,<:SymmetricPositiveDefinite,LogCholeskyMetric}, p, X, Y)
```

Compute the inner product of two matrices `X`, `Y` in the tangent space of `p` on the [`SymmetricPositiveDefinite`](@ref) manifold `M`, as a [`MetricManifold`](@ref) with [`LogCholeskyMetric`](@ref). The formula reads

$$
    g_p(X,Y) = ⟨a_z(X),a_z(Y)⟩_z,
$$

where $⟨⋅,⋅⟩_x$ denotes inner product on the [`CholeskySpace`](@ref), $z$ is the Cholesky factor of $p$, $a_z(W) = z (z^{-1}Wz^{-\mathrm{T}})_{\frac{1}{2}}$, and $(⋅)_\frac{1}{2}$ denotes the lower triangular matrix with the diagonal multiplied by $\frac{1}{2}$
