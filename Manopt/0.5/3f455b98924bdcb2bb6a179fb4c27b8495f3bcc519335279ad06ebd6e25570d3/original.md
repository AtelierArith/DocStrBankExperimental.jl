```
get_cost(TpM, trmo::TrustRegionModelObjective, X)
```

Evaluate the tangent space [`TrustRegionModelObjective`](@ref)

$$
m(X) = f(p) + ⟨\operatorname{grad} f(p), X ⟩_p + \frac{1}{2} ⟨\operatorname{Hess} f(p)[X], X⟩_p.
$$
