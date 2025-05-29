```
workspace = cg_lanczos!(workspace::CgLanczosWorkspace, A, b; kwargs...)
workspace = cg_lanczos!(workspace::CgLanczosWorkspace, A, b, x0; kwargs...)
```

In these calls, `kwargs` are keyword arguments of [`cg_lanczos`](@ref).

See [`CgLanczosWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :cg_lanczos` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
