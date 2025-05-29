```
constraints_flow_in(m, n, 𝒯::TimeStructure, modeltype::EnergyModel)
constraints_flow_in(m, n::Storage, 𝒯::TimeStructure, modeltype::EnergyModel)
constraints_flow_in(m, n::Storage{AccumulatingEmissions}, 𝒯::TimeStructure, modeltype::EnergyModel)
```

Function for creating the constraint on the outlet flow from a generic [`Node`](@ref) or [`Storage`](@ref).

These functions serve as fallback option if no other method is specified for a specific `Node`.
