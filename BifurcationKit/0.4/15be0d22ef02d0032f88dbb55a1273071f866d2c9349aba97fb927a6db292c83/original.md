```julia
continuation(
    coll,
    orbitguess,
    alg,
    _contParams,
    linear_algo;
    δ,
    eigsolver,
    record_from_solution,
    plot_solution,
    kwargs...
)

```

This is the continuation method for computing a periodic orbit using an orthogonal collocation method.

# Arguments

Similar to [`continuation`](@ref) except that `prob` is a [`PeriodicOrbitOCollProblem`](@ref). By default, it prints the period of the periodic orbit.

# Keywords arguments

  * `eigsolver` specify an eigen solver for the computation of the Floquet exponents, defaults to `FloquetQaD`
