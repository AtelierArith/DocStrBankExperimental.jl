```
dual_status(model::Model; result::Int = 1)
```

Return a [`MOI.ResultStatusCode`](@ref) describing the status of the most recent dual solution of the solver (i.e., the [`MOI.DualStatus`](@ref) attribute) associated with the result index `result`.

See also: [`result_count`](@ref).
