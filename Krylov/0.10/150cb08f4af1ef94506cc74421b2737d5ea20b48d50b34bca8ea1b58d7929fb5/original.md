```
workspace = diom!(workspace::DiomWorkspace, A, b; kwargs...)
workspace = diom!(workspace::DiomWorkspace, A, b, x0; kwargs...)
```

In these calls, `kwargs` are keyword arguments of [`diom`](@ref). The keyword argument `memory` is the only exception. It is only supported by `diom` and is required to create a `DiomWorkspace`. It cannot be changed later.

See [`DiomWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :diom` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
