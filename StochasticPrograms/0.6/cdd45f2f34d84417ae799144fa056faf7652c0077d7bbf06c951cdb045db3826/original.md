```
objective_function(stochasticprogram::StochasticProgram,
                   T::Type{<:AbstractJuMPScalar}=objective_function_type(model))
```

Return an object of type `T` representing the full objective function of the `stochasticprogram`. Error if the objective is not convertible to type `T`.
