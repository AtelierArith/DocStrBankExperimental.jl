```
workspace = symmlq!(workspace::SymmlqWorkspace, A, b; kwargs...)
workspace = symmlq!(workspace::SymmlqWorkspace, A, b, x0; kwargs...)
```

In these calls, `kwargs` are keyword arguments of [`symmlq`](@ref).

See [`SymmlqWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :symmlq` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
