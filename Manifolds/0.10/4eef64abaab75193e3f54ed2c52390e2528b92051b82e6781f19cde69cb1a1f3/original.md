```
exp(::MatricManifold{ℝ,SymmetricPositiveDefinite,BuresWassersteinMetric}, p, X)
```

Compute the exponential map on [`SymmetricPositiveDefinite`](@ref) with respect to the [`BuresWassersteinMetric`](@ref) given by

$$
    \exp_p(X) = p+X+L_p(X)pL_p(X)
$$

where $q=L_p(X)$ denotes the Lyapunov operator, i.e. it solves $pq + qp = X$.
