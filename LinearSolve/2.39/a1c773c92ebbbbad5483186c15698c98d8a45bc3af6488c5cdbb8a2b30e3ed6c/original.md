```julia
KrylovKitJL(args...; KrylovAlg = Krylov.gmres!, kwargs...)
```

A generic iterative solver implementation allowing the choice of KrylovKit.jl solvers.

!!! note
    Using this solver requires adding the package KrylovKit.jl, i.e. `using KrylovKit`

