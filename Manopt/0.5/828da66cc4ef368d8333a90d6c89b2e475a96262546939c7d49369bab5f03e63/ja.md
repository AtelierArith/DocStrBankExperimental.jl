```
get_hess_inequality_constraint(amp::AbstractManoptProblem, p, X, j=:)
get_hess_inequality_constraint(M::AbstractManifold, co::ConstrainedManifoldObjective, p, j=:, range=NestedPowerRepresentation())
get_hess_inequality_constraint!(amp::AbstractManoptProblem, Y, p, j=:)
get_hess_inequality_constraint!(M::AbstractManifold, Y, co::ConstrainedManifoldObjective, p, X, j=:, range=NestedPowerRepresentation())
```

不等式制約のヘッセ行列またはヘッセ行列を評価します $(\operatorname{Hess} g(p)[X])_j$ または $\operatorname{Hess} g_j(p)[X]$、

ヘッセ行列の範囲を指定するには、[`ConstrainedManoptProblem`](@ref)も参照してください。
