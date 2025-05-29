```
set_time_limit_sec(model::Model, limit::Float64)
```

Set the time limit (in seconds) of the solver.

Can be unset using [`unset_time_limit_sec`](@ref) or with `limit` set to `nothing`.

See also: [`unset_time_limit_sec`](@ref), [`time_limit_sec`](@ref).
