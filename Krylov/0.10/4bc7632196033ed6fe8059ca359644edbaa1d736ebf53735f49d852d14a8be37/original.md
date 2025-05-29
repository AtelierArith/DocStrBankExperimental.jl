```
workspace = cg!(workspace::CgWorkspace, A, b; kwargs...)
workspace = cg!(workspace::CgWorkspace, A, b, x0; kwargs...)
```

In these calls, `kwargs` are keyword arguments of [`cg`](@ref).

See [`CgWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :cg` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
