```
add_ineq_constraint!(model::AbstractModel, f::IneqConstraint)
add_ineq_constraint!(model::AbstractModel, fs::Vector{<:IneqConstraint})
```

モデルに新しい制約 `f` または複数の新しい制約 `fs` を追加します。
