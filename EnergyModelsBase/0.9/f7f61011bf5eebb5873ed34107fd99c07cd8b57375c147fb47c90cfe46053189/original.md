```
constraints_flow_out(m, n::Node, 𝒯::TimeStructure, modeltype::EnergyModel)
constraints_flow_out(m, n::Storage, 𝒯::TimeStructure, modeltype::EnergyModel)
```

Function for creating the constraint on the outlet flow from a generic `Node`. This function serves as fallback option if no other function is specified for a `Node`.
