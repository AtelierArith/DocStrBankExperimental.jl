```
add_ineq_constraint!(model::AbstractModel, f::IneqConstraint)
add_ineq_constraint!(model::AbstractModel, fs::Vector{<:IneqConstraint})
```

Adds a new constraint `f` or multiple new constraints `fs` to `model`.
