```julia
PDESystem(
;
    A,
    b,
    bc,
    DI,
    qdim,
    Factors,
    SystemMatrix,
    B,
    state,
    rhs
) -> MinFEM.PDESystem

```

Constructor for [PDESystem](@ref). Allows to specify all fields by keyword arguments.
