```
value(v::GenericQuadExpr; result::Int = 1)
```

Return the value of the `GenericQuadExpr` `v` associated with result index `result` of the most-recent solution returned by the solver.

Replaces `getvalue` for most use cases.

See also: [`result_count`](@ref).
