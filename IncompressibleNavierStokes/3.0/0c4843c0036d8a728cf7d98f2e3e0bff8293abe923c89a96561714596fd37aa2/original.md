```julia
psolver_cg_matrix(
    setup;
    kwargs...
) -> IncompressibleNavierStokes.var"#psolve!#104"{Base.Pairs{Symbol, Union{}, Tuple{}, @NamedTuple{}}}

```

Conjugate gradients iterative Poisson solver. The `kwargs` are passed to the `cg!` function from IterativeSolvers.jl.
