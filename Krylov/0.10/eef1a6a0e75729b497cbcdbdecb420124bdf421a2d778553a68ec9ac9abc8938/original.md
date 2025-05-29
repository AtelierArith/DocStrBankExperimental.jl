```
workspace = dqgmres!(workspace::DqgmresWorkspace, A, b; kwargs...)
workspace = dqgmres!(workspace::DqgmresWorkspace, A, b, x0; kwargs...)
```

In these calls, `kwargs` are keyword arguments of [`dqgmres`](@ref). The keyword argument `memory` is the only exception. It is only supported by [`dqgmres`](@ref) and is required to create a `DqgmresWorkspace`. It cannot be changed later.

See [`DqgmresWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :dqgmres` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
