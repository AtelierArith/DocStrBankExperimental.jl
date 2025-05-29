```
workspace = bicgstab!(workspace::BicgstabWorkspace, A, b; kwargs...)
workspace = bicgstab!(workspace::BicgstabWorkspace, A, b, x0; kwargs...)
```

In these calls, `kwargs` are keyword arguments of [`bicgstab`](@ref).

See [`BicgstabWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :bicgstab` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
