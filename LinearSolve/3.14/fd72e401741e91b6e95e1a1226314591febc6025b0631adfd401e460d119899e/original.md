```julia
KrylovJL(args...; KrylovAlg = Krylov.gmres!,
    Pl = nothing, Pr = nothing,
    gmres_restart = 0, window = 0,
    kwargs...)
```

A generic wrapper over the Krylov.jl krylov-subspace iterative solvers.
