```
set_objective_function(
    model::Model,
    func::Union{AbstractJuMPScalar, MathOptInterface.AbstractScalarFunction})
```

Sets the objective function of the model to the given function. See [`set_objective_sense`](@ref) to set the objective sense. These are low-level functions; the recommended way to set the objective is with the [`@objective`](@ref) macro.
