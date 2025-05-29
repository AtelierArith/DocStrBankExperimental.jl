```
has_values(model::Model; result::Int = 1)
```

Return `true` if the solver has a primal solution in result index `result` available to query, otherwise return `false`.

See also [`value`](@ref) and [`result_count`](@ref).
