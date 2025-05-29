```julia
IterativeSolversJL(args...;
    generate_iterator = IterativeSolvers.gmres_iterable!,
    Pl = nothing, Pr = nothing,
    gmres_restart = 0, kwargs...)
```

A generic wrapper over the IterativeSolvers.jl solvers.

!!! note
    Using this solver requires adding the package IterativeSolvers.jl, i.e. `using IterativeSolvers`

