```
dual(con_ref::ConstraintRef; result::Int = 1)
```

Return the dual value of constraint `con_ref` associated with result index `result` of the most-recent solution returned by the solver.

Use `has_dual` to check if a result exists before asking for values.

See also: [`result_count`](@ref), [`shadow_price`](@ref).
