```
workspace = usymqr!(workspace::UsymqrWorkspace, A, b, c; kwargs...)
workspace = usymqr!(workspace::UsymqrWorkspace, A, b, c, x0; kwargs...)
```

In these calls, `kwargs` are keyword arguments of [`usymqr`](@ref).

See [`UsymqrWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :usymqr` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
