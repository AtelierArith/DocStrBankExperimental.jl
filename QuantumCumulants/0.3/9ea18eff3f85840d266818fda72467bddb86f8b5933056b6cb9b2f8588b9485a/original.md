```
numeric_average(avg::Average, state; level_map = nothing)
numeric_average(q::QNumber, state; level_map = nothing)
```

From a symbolic average `avg` or operator `q`, compute the corresponding numerical average value with the given quantum state `state`. This state can either be of type `QuantumOpticsBase.StateVector` or `QuantumOpticsBase.Operator`.

See also: [`initial_values`](@ref), [`to_numeric`](@ref)
