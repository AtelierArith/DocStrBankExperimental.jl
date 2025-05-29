```
workspace = cgs!(workspace::CgsWorkspace, A, b; kwargs...)
workspace = cgs!(workspace::CgsWorkspace, A, b, x0; kwargs...)
```

In these calls, `kwargs` are keyword arguments of [`cgs`](@ref).

See [`CgsWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :cgs` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
