```
constraints_opex_fixed(m, n::Node, 𝒯ᴵⁿᵛ, modeltype::EnergyModel)
constraints_opex_fixed(m, n::Storage, 𝒯ᴵⁿᵛ, modeltype::EnergyModel)
constraints_opex_fixed(m, n::Sink, 𝒯ᴵⁿᵛ, modeltype::EnergyModel)
```

Function for creating the constraint on the fixed OPEX of a generic [`Node`](@ref), [`Storage`](@ref), and [`Sink`](@ref).

This function serves as fallback option if no other method is specified for a `Node`.

The fallback option for `Storage` nodes includes fixed OPEX for `charge`, `level`, and `discharge` if the node has the corresponding storage parameter. The individual contributions are in all situations calculated based on the installed capacities.

In the case of a `Storage` node, the fallback option includes fixed OPEX for `charge`, `level`, and `discharge` if the node has the corresponding storage parameter. The individual contributions are in all situations calculated based on the installed capacities.

In the case of a `Sink` node, the fallback option fixes the value of the variable `:opex_fixed` to 0.
