```
inner(::MetricManifold{ℝ,SymmetricPositiveDefinite,BuresWassersteinMetric}, p, X, Y)
```

Compute the inner product [`SymmetricPositiveDefinite`](@ref) with respect to the [`BuresWassersteinMetric`](@ref) given by

$$
    ⟨X,Y⟩ = \frac{1}{2}\operatorname{tr}(L_p(X)Y)
$$

where $q=L_p(X)$ denotes the Lyapunov operator, i.e. it solves $pq + qp = X$.
