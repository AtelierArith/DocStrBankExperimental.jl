```
get_gradient(M::AbstractManifold, scaled_objective::ScaledManifoldObjective, p)
get_gradient!(M::AbstractManifold, X, scaled_objective::ScaledManifoldObjective, p)
```

スケーリングされた勾配を評価します。 $s*\operatorname{grad}f(p)$
