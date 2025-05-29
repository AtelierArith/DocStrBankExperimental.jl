```
get_hess_equality_constraint(amp::AbstractManoptProblem, p, j=:)
get_hess_equality_constraint(M::AbstractManifold, co::ConstrainedManifoldObjective, p, j, range=NestedPowerRepresentation())
get_hess_equality_constraint!(amp::AbstractManoptProblem, X, p, j=:)
get_hess_equality_constraint!(M::AbstractManifold, X, co::ConstrainedManifoldObjective, p, j, range=NestedPowerRepresentation())
```

等式制約のヘッセ行列またはヘッセ行列を評価します $(\operatorname{Hess} h(p))_j$ または $\operatorname{Hess} h_j(p)$、

ヘッセ行列の範囲を指定するには、[`ConstrainedManoptProblem`](@ref)を参照してください。
