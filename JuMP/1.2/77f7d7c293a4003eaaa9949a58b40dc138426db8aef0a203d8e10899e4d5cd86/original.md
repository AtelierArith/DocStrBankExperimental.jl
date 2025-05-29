```
value(v::VariableRef; result = 1)
```

Return the value of variable `v` associated with result index `result` of the most-recent returned by the solver.

Use [`has_values`](@ref) to check if a result exists before asking for values.

See also: [`result_count`](@ref).
