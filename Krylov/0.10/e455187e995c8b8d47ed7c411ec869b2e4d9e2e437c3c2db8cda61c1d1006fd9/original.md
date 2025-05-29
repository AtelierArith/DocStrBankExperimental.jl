```
workspace = lsmr!(workspace::LsmrWorkspace, A, b; kwargs...)
```

In this call, `kwargs` are keyword arguments of [`lsmr`](@ref).

See [`LsmrWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :lsmr` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
