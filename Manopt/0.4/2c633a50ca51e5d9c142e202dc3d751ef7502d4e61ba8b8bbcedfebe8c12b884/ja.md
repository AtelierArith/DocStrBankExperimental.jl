```
get_equality_constraint(amp::AbstractManoptProblem, p, j=:)
get_equality_constraint(M::AbstractManifold, objective, p, j=:)
```

点 `p` およびインデックス `j`（デフォルトは `:` で、すべてのインデックスに対応）での [`ConstrainedManifoldObjective`](@ref) `objective` の等式制約を評価します。
