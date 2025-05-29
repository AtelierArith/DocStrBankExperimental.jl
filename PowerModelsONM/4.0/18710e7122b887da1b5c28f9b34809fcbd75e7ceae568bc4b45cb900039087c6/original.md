```
build_solver_instances!(args::Dict{String,<:Any})::Dict{String,Any}
```

Creates the Optimizers in-place (within the args dict data structure), for use inside [`entrypoint`](@ref entrypoint), using [`build_solver_instances`](@ref build_solver_instances), assigning them to `args["solvers"]``
