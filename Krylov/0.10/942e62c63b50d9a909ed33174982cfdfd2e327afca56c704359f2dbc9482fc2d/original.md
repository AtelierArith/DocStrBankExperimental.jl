```
workspace = car!(workspace::CarWorkspace, A, b; kwargs...)
workspace = car!(workspace::CarWorkspace, A, b, x0; kwargs...)
```

In these calls, `kwargs` are keyword arguments of [`car`](@ref).

See [`CarWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :car` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
