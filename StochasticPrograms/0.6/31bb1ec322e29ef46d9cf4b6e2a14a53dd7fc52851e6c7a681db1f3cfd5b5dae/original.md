```
objective_function(stochasticprogram::StochasticProgram,
                   stage::Integer,
                   scenario_index::Integer,
                   T::Type{<:AbstractJuMPScalar}=objective_function_type(model))
```

Return an object of type `T` representing the objective function in the node at stage `stage` and scenario `scenario_index`. Error if the objective is not convertible to type `T`.
