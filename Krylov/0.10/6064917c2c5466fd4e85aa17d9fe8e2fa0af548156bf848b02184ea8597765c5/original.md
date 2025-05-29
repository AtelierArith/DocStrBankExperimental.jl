```
workspace = cgls_lanczos_shift!(workspace::CglsLanczosShiftWorkspace, A, b, shifts; kwargs...)
```

In this call, `kwargs` are keyword arguments of [`cgls_lanczos_shift`](@ref).

See [`CglsLanczosShiftWorkspace`](@ref) for instructions on how to create the `workspace`.

For a more generic interface, you can use [`krylov_workspace`](@ref) with `method = :cgls_lanczos_shift` to allocate the workspace, and [`krylov_solve!`](@ref) to run the Krylov method in-place.
