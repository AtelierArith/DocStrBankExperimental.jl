```
workspace = trilqr!(workspace::TrilqrWorkspace, A, b, c; kwargs...)
workspace = trilqr!(workspace::TrilqrWorkspace, A, b, c, x0, y0; kwargs...)
```

In these calls, `kwargs` are keyword arguments of [`trilqr`](@ref).

See [`TrilqrWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :trilqr` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
