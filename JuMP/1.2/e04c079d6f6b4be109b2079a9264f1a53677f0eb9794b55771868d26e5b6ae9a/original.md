```
dual_objective_value(model::Model; result::Int = 1)
```

Return the value of the objective of the dual problem associated with result index `result` of the most-recent solution returned by the solver.

Throws `MOI.UnsupportedAttribute{MOI.DualObjectiveValue}` if the solver does not support this attribute.

See also: [`result_count`](@ref).
