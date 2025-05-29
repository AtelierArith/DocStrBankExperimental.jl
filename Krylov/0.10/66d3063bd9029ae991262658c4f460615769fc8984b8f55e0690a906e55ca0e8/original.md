```
workspace = fom!(workspace::FomWorkspace, A, b; kwargs...)
workspace = fom!(workspace::FomWorkspace, A, b, x0; kwargs...)
```

In these calls, `kwargs` are keyword arguments of [`fom`](@ref). The keyword argument `memory` is the only exception. It is only supported by [`fom`](@ref) and is required to create a `FomWorkspace`. It cannot be changed later.

See [`FomWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :fom` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
