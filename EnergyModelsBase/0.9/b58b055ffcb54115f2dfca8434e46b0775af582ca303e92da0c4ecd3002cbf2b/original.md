```
constraints_capacity_installed(m, n::Node, 𝒯::TimeStructure, modeltype::EnergyModel)
constraints_capacity_installed(m, n::Storage, 𝒯::TimeStructure, modeltype::EnergyModel)
constraints_capacity_installed(m, l::Link, 𝒯::TimeStructure, modeltype::EnergyModel)
```

Function for creating the constraint on the installed capacity to the available capacity.

These functions serve as fallback option if no other method is specified for a specific `Node` or `Link`.

!!! danger "Dispatching on this function"
    This function should only be used to dispatch on the modeltype for providing investments. If you create new capacity variables (as it is the case for storage nodes), it is beneficial to include as well a method for this function and the corresponding node types.

