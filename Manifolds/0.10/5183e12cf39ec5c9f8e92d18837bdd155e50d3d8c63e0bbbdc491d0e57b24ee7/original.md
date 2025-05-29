```
inner(::SymplecticMatrices{<:Any,ℝ}, p, X, Y)
```

Compute the canonical Riemannian inner product [`RealSymplecticMetric`](@ref)

$$
    g_p(X, Y) = \operatorname{tr}((p^{-1}X)^{\mathrm{T}} (p^{-1}Y))
$$

between the two tangent vectors $X, Y \in T_p\mathrm{Sp}(2n)$.
