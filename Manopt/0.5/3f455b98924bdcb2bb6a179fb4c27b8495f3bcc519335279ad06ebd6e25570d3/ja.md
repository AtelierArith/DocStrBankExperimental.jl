```
get_cost(TpM, trmo::TrustRegionModelObjective, X)
```

接触空間 [`TrustRegionModelObjective`](@ref) を評価します。

$$
m(X) = f(p) + ⟨\operatorname{grad} f(p), X ⟩_p + \frac{1}{2} ⟨\operatorname{Hess} f(p)[X], X⟩_p.
$$
