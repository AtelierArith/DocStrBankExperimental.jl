```
workspace = fgmres!(workspace::FgmresWorkspace, A, b; kwargs...)
workspace = fgmres!(workspace::FgmresWorkspace, A, b, x0; kwargs...)
```

In these calls, `kwargs` are keyword arguments of [`fgmres`](@ref). The keyword argument `memory` is the only exception. It is only supported by [`fgmres`](@ref) and is required to create a `FgmresWorkspace`. It cannot be changed later.

See [`FgmresWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :fgmres` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
