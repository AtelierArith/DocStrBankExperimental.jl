```julia
parameter_bounds(
    _::ContinuumMechanicsBase.AbstractMaterialModel,
    _::ContinuumMechanicsBase.AbstractMaterialTest
) -> @NamedTuple{lb::Nothing, ub::Nothing}

```

Default bounds for each parameter in tuple for optimization. Without method dispatching for certain models, constants can be "optimized" in the range [-∞, ∞]. Use discretion whether this is realistic.
