```
workspace = craigmr!(workspace::CraigmrWorkspace, A, b; kwargs...)
```

In this call, `kwargs` are keyword arguments of [`craigmr`](@ref).

See [`CraigmrWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :craigmr` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
