```
has_duals(model::Model; result::Int = 1)
```

Return `true` if the solver has a dual solution in result index `result` available to query, otherwise return `false`.

See also [`dual`](@ref), [`shadow_price`](@ref), and [`result_count`](@ref).
