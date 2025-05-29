```
log(::MatricManifold{SymmetricPositiveDefinite,BuresWassersteinMetric}, p, q)
```

Compute the logarithmic map on [`SymmetricPositiveDefinite`](@ref) with respect to the [`BuresWassersteinMetric`](@ref) given by

$$
    \log_p(q) = (pq)^{\frac{1}{2}} + (qp)^{\frac{1}{2}} - 2 p
$$

where $q=L_p(X)$ denotes the Lyapunov operator, i.e. it solves $pq + qp = X$.
