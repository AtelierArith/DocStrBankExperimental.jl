```julia
generate_initializesystem(
    sys::ModelingToolkit.AbstractTimeIndependentSystem;
    u0map,
    pmap,
    initialization_eqs,
    guesses,
    algebraic_only,
    check_units,
    check_defguess,
    name,
    kwargs...
) -> ModelingToolkit.NonlinearSystem

```

Generate `NonlinearSystem` which initializes a problem from specified initial conditions of an `AbstractTimeDependentSystem`.
