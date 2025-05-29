```
create_node(m, n::Sink, 𝒯, 𝒫, modeltype::EnergyModel)
```

Set all constraints for a `Sink`. Can serve as fallback option for all unspecified subtypes of `Sink`.

# Called constraint functions

  * [`constraints_data`](@ref) for all `node_data(n)`,
  * [`constraints_flow_in`](@ref),
  * [`constraints_capacity`](@ref),
  * [`constraints_opex_fixed`](@ref), and
  * [`constraints_opex_var`](@ref).
