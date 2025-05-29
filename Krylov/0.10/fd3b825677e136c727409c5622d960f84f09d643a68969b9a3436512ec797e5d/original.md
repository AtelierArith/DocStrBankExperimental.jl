```
workspace = cr!(workspace::CrWorkspace, A, b; kwargs...)
workspace = cr!(workspace::CrWorkspace, A, b, x0; kwargs...)
```

In these calls, `kwargs` are keyword arguments of [`cr`](@ref).

See [`CrWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :cr` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
