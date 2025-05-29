```
workspace = gmres!(workspace::GmresWorkspace, A, b; kwargs...)
workspace = gmres!(workspace::GmresWorkspace, A, b, x0; kwargs...)
```

In these calls, `kwargs` are keyword arguments of [`gmres`](@ref). The keyword argument `memory` is the only exception. It is only supported by [`gmres`](@ref) and is required to create a `GmresWorkspace`. It cannot be changed later.

See [`GmresWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :gmres` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
