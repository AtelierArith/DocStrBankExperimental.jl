```
create_node(m, n::Storage, 𝒯, 𝒫, modeltype::EnergyModel)
```

Set all constraints for a `Storage`. Can serve as fallback option for all unspecified subtypes of `Storage`.

# Called constraint functions

  * [`constraints_level`](@ref)
  * [`constraints_data`](@ref) for all `node_data(n)`,
  * [`constraints_flow_in`](@ref),
  * [`constraints_flow_out`](@ref),
  * [`constraints_capacity`](@ref),
  * [`constraints_opex_fixed`](@ref), and
  * [`constraints_opex_var`](@ref).
