```
workspace = gpmr!(workspace::GpmrWorkspace, A, B, b, c; kwargs...)
workspace = gpmr!(workspace::GpmrWorkspace, A, B, b, c, x0, y0; kwargs...)
```

In these calls, `kwargs` are keyword arguments of [`gpmr`](@ref). The keyword argument `memory` is the only exception. It is only supported by [`gpmr`](@ref) and is required to create a `GpmrWorkspace`. It cannot be changed later.

See [`GpmrWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :gpmr` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
