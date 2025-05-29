```
workspace = minares!(workspace::MinaresWorkspace, A, b; kwargs...)
workspace = minares!(workspace::MinaresWorkspace, A, b, x0; kwargs...)
```

In these calls, `kwargs` are keyword arguments of [`minares`](@ref).

See [`MinaresWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :minares` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
