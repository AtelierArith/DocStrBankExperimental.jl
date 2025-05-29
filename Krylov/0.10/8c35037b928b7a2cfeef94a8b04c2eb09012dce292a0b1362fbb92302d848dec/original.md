```
workspace = qmr!(workspace::QmrWorkspace, A, b; kwargs...)
workspace = qmr!(workspace::QmrWorkspace, A, b, x0; kwargs...)
```

In these calls, `kwargs` are keyword arguments of [`qmr`](@ref).

See [`QmrWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :qmr` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
