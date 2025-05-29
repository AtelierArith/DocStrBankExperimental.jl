```
workspace = cg_lanczos_shift!(workspace::CgLanczosShiftWorkspace, A, b, shifts; kwargs...)
```

In this call, `kwargs` are keyword arguments of [`cg_lanczos_shift`](@ref).

See [`CgLanczosShiftWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :cg_lanczos_shift` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
