```
get_inequality_constraint(amp::AbstractManoptProblem, p, j=:)
get_inequality_constraint(M::AbstractManifold, co::ConstrainedManifoldObjective, p, j=:, range=NestedPowerRepresentation())
```

点 `p` およびインデックス `j`（デフォルトは `:` で、すべてのインデックスに対応）で [`ConstrainedManifoldObjective`](@ref) `objective` の不等式制約を評価します。
