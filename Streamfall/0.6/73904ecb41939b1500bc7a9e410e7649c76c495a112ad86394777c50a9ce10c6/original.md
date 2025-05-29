```
run_node!(
    node::DamNode,
    ts::Int64,
    rain::Float64,
    et::Float64,
    volume::Float64,
    inflow::Float64,
    extractions::Float64,
    gw_flux::Float64
)
```

Calculate outflow for the dam node for a single time step.

# Arguments

  * `node` : DamNode
  * `rain` : rainfall in mm
  * `et` : evapotranspiration data in mm
  * `irrig_ext` : irrigation extractions
  * `extractions` : extraction data in ML
  * `gw_flux` : groundwater interaction

# Returns

Outflow from dam
