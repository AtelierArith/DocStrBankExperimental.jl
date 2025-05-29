```
krylov_solve!(workspace, args...; kwargs...)
```

Generic function that dispatches to the appropriate in-place (block) Krylov method based on the type of `workspace`. The argument `workspace` must be a subtype of [`KrylovWorkspace`](@ref) or [`BlockKrylovWorkspace`](@ref) (such as `CgWorkspace`, `GmresWorkspace` or `BlockMinresWorkspace`).
