```
get_hessian(M::AbstractManifold, scaled_objective::ScaledManifoldObjective, p, X)
get_hessian!(M::AbstractManifold, Y, scaled_objective::ScaledManifoldObjective, p, X)
```

Evaluate the scaled Hessian $s*\operatorname{Hess}f(p)$
