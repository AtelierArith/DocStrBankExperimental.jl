```julia
generate_initializesystem(
    sys::ModelingToolkit.AbstractTimeDependentSystem;
    u0map,
    pmap,
    initialization_eqs,
    guesses,
    default_dd_guess,
    algebraic_only,
    check_units,
    check_defguess,
    name,
    kwargs...
) -> ModelingToolkit.NonlinearSystem

```

Generate `NonlinearSystem` which initializes a problem from specified initial conditions of an `AbstractTimeDependentSystem`.
