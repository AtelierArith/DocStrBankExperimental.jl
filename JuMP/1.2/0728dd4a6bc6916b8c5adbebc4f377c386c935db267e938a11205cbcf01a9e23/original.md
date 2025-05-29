```
primal_status(model::Model; result::Int = 1)
```

Return a [`MOI.ResultStatusCode`](@ref) describing the status of the most recent primal solution of the solver (i.e., the [`MOI.PrimalStatus`](@ref) attribute) associated with the result index `result`.

See also: [`result_count`](@ref).
