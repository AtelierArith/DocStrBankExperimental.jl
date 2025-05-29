```
get_gradient(TpM, trmo::TrustRegionModelObjective, X)
```

Evaluate the gradient of the [`TrustRegionModelObjective`](@ref)

$$
\operatorname{grad} m(X) = \operatorname{grad} f(p) + \operatorname{Hess} f(p)[X].
$$
