```julia
convert_system(
    ::Type{<:ModelingToolkit.ODESystem},
    sys,
    t;
    name
) -> ModelingToolkit.ODESystem

```

Convert a `NonlinearSystem` to an `ODESystem` or converts an `ODESystem` to a new `ODESystem` with a different independent variable.
