```
constraints_opex_var(m, n::Node, 𝒯ᴵⁿᵛ, modeltype::EnergyModel)
constraints_opex_var(m, n::Storage, 𝒯ᴵⁿᵛ, modeltype::EnergyModel)
constraints_opex_var(m, n::Sink, 𝒯ᴵⁿᵛ, modeltype::EnergyModel)
```

Function for creating the constraint on the variable OPEX of a generic [`Node`](@ref), [`Storage`](@ref), and [`Sink`](@ref).

This function serves as fallback option if no other method is specified for a `Node`.

In the case of a `Storage` node, the fallback option includes variable OPEX for `charge`, `level`, and `discharge` if the node has the corresponding storage parameter. The individual contributions are in all situations calculated based on the installed capacities.

In the case of a `Sink` node, the variable OPEX is calculate through the penalties for both `surplus` and `deficit`.
