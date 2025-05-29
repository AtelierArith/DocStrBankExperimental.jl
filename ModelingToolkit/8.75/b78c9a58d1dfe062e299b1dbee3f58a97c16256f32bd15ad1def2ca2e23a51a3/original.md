```julia
initializesystem(
    sys::ModelingToolkit.ODESystem;
    name,
    kwargs...
) -> ModelingToolkit.NonlinearSystem

```

Generate `NonlinearSystem` which initializes an ODE problem from specified initial conditions of an `ODESystem`.
