```
create_node(m, n::Source, 𝒯, 𝒫, modeltype::EnergyModel)
```

Set all constraints for a `Source`. Can serve as fallback option for all unspecified subtypes of `Source`.

# Called constraint functions

  * [`constraints_data`](@ref) for all `node_data(n)`,
  * [`constraints_flow_out`](@ref),
  * [`constraints_capacity`](@ref),
  * [`constraints_opex_fixed`](@ref), and
  * [`constraints_opex_var`](@ref).
