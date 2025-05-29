```
HydroGate <: EMB.NetworkNode
```

A hydro gate, modelled as a `NetworkNode` node.

It an be used to model outlets/inlets and minimum/maximum requirements for water flow between individual reservoirs without power generation.

## Fields

  * **`id`** is the name/identifier of the node.
  * **`cap::TimeProfile`** is the installed discharge capacity.
  * **`opex_var::TimeProfile`** is the variational operational costs per water flow through the gate.
  * **`opex_fixed::TimeProfile`** is the fixed operational costs.
  * **`resource::ResourceCarrier`** is the water resource type since gates are only used for discharging water.
  * **`data::Vector{<:Data}`** is the additional data (*e.g.*, for investments or constraints through [`AbstractScheduleType`](@ref)). The field `data` is conditional through usage of a constructor.
