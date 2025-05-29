```
get_hessian(M::AbstractManifold, scaled_objective::ScaledManifoldObjective, p, X)
get_hessian!(M::AbstractManifold, Y, scaled_objective::ScaledManifoldObjective, p, X)
```

スケーリングされたヘッセ行列 $s*\operatorname{Hess}f(p)$ を評価します。
