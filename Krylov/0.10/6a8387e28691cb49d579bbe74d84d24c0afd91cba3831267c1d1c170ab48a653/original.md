```
workspace = minres_qlp!(workspace::MinresQlpWorkspace, A, b; kwargs...)
workspace = minres_qlp!(workspace::MinresQlpWorkspace, A, b, x0; kwargs...)
```

In these calls, `kwargs` are keyword arguments of [`minres_qlp`](@ref).

See [`MinresQlpWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :minres_qlp` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
