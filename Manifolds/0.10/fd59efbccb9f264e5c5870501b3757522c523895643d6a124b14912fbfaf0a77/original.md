```
inner(::MetricManifold{ℝ,<:SymmetricPositiveDefinite,<:GeneralizedBuresWassersteinMetric}, p, X, Y)
```

Compute the inner product [`SymmetricPositiveDefinite`](@ref) with respect to the [`GeneralizedBuresWassersteinMetric`](@ref) given by

$$
    ⟨X,Y⟩ = \frac{1}{2}\operatorname{tr}(L_{p,M}(X)Y)
$$

where $q=L_{M,p}(X)$ denotes the generalized Lyapunov operator, i.e. it solves $pqM + Mqp = X$.
