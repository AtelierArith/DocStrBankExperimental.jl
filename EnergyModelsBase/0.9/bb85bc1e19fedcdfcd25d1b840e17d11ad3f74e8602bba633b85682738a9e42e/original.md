```
constraints_capacity(m, n::Node, 𝒯::TimeStructure, modeltype::EnergyModel)
constraints_capacity(m, n::Storage, 𝒯::TimeStructure, modeltype::EnergyModel)
constraints_capacity(m, n::Sink, 𝒯::TimeStructure, modeltype::EnergyModel)
```

Function for creating the constraints on the maximum capacity of a generic [`Node`](@ref), [`Storage`](@ref), and [`Sink`](@ref).

These functions serve as fallback option if no other method is specified for a specific `Node`.

!!! warning "Dispatching on this function"
    If you create a new method for this function, it is crucial to call within said function the function `constraints_capacity_installed(m, n, 𝒯, modeltype)` if you want to include investment options.

