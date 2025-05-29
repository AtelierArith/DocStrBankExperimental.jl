```
workspace = block_gmres!(workspace::BlockGmresWorkspace, B; kwargs...)
workspace = block_gmres!(workspace::BlockGmresWorkspace, B, X0; kwargs...)
```

In these calls, `kwargs` are keyword arguments of [`block_gmres`](@ref). The keyword argument `memory` is the only exception. It is only supported by `block_gmres` and is required to create a `BlockGmresWorkspace`. It cannot be changed later.

See [`BlockGmresWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :block_gmres` to allocate the workspace, and [`krylov_solve!`](@ref) to run the block Krylov method in-place.
