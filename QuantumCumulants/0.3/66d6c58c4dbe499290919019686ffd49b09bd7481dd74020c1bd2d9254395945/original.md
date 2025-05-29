```
initial_values(eqs::MeanfieldEquations, state; level_map=nothing)
```

For a set of symbolic equations `eqs` compute the initial state average values corresponding to the numeric quantum state `state` of the system. The quantum state can either be of type `QuantumOpticsBase.StateVector` or `QuantumOpticsBase.Operator`.

See also: [`to_numeric`](@ref), [`numeric_average`](@ref)
