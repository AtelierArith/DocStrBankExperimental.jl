```
get_gradient(M::AbstractManifold, scaled_objective::ScaledManifoldObjective, p)
get_gradient!(M::AbstractManifold, X, scaled_objective::ScaledManifoldObjective, p)
```

Evaluate the scaled gradient. $s*\operatorname{grad}f(p)$
