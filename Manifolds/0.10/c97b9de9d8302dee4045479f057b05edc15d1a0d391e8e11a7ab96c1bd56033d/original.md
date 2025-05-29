```
exp(M::SymplecticMatrices, p, X)
exp!(M::SymplecticMatrices, q, p, X)
```

The Exponential mapping on the Symplectic manifold with the [`RealSymplecticMetric`](@ref) Riemannian metric.

For the point $p \in \mathrm{Sp}(2n)$ the exponential mapping along the tangent vector $X \in T_p\mathrm{Sp}(2n)$ is computed as [WangSunFiori:2018](@cite)

$$
    \operatorname{exp}_p(X) = p \operatorname{Exp}((p^{-1}X)^{\mathrm{T}})
                                \operatorname{Exp}(p^{-1}X - (p^{-1}X)^{\mathrm{T}}),
$$

where $\operatorname{Exp}(⋅)$ denotes the matrix exponential.
