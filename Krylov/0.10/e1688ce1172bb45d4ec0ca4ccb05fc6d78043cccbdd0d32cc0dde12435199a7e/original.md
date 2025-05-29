```
workspace = lnlq!(workspace::LnlqWorkspace, A, b; kwargs...)
```

In this call, `kwargs` are keyword arguments of [`lnlq`](@ref).

See [`LnlqWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :lnlq` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
