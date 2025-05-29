```
workspace = block_minres!(workspace::BlockMinresWorkspace, B; kwargs...)
workspace = block_minres!(workspace::BlockMinresWorkspace, B, X0; kwargs...)
```

In these calls, `kwargs` are keyword arguments of [`block_minres`](@ref).

See [`BlockMinresWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :block_minres` to allocate the workspace, and [`krylov_solve!`](@ref) to run the block Krylov method in-place.
