```
workspace = bilq!(workspace::BilqWorkspace, A, b; kwargs...)
workspace = bilq!(workspace::BilqWorkspace, A, b, x0; kwargs...)
```

In these calls, `kwargs` are keyword arguments of [`bilq`](@ref).

See [`BilqWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :bilq` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
