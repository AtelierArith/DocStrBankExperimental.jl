```
objective_function(stochasticprogram::StochasticProgram,
                   stage::Integer,
                   T::Type{<:AbstractJuMPScalar}=objective_function_type(model))
```

Return an object of type `T` representing the objective function at stage `stage` of the `stochasticprogram`. Error if the objective is not convertible to type `T`.
