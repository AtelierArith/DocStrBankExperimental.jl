```
get_grad_inequality_constraint(amp::AbstractManoptProblem, p, j=:)
get_grad_inequality_constraint(M::AbstractManifold, co::ConstrainedManifoldObjective, p, j=:, range=NestedPowerRepresentation())
get_grad_inequality_constraint!(amp::AbstractManoptProblem, X, p, j=:)
get_grad_inequality_constraint!(M::AbstractManifold, X, co::ConstrainedManifoldObjective, p, j=:, range=NestedPowerRepresentation())
```

不等式制約の勾配または勾配を評価します $(\operatorname{grad} g(p))_j$ または $\operatorname{grad} g_j(p)$、

勾配の範囲を指定するには、[`ConstrainedManoptProblem`](@ref)も参照してください。
