```
set_default_solver_view!(model, modeldata)
```

(Optional, used to set `modeldata.solver_view_all` to a [`SolverView`](@ref)) for the whole model, and set `modeldata.hostdep_data` to any non-state-variable host dependent Variables)

`reallocate_hostdep_eltype` a data type to reallocate `hostdep_data` eg to replace any AD types.
