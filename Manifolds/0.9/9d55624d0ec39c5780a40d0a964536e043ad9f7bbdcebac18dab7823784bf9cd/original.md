```
exp(::MatricManifold{ℝ,<:SymmetricPositiveDefinite,<:GeneralizedBuresWassersteinMetric}, p, X)
```

Compute the exponential map on [`SymmetricPositiveDefinite`](@ref) with respect to the [`GeneralizedBuresWassersteinMetric`](@ref) given by

$$
    \exp_p(X) = p+X+\mathcal ML_{p,M}(X)pML_{p,M}(X)
$$

where $q=L_{M,p}(X)$ denotes the generalized Lyapunov operator, i.e. it solves $pqM + Mqp = X$.
