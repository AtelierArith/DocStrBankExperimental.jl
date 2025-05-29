```
HydroGenerator <: HydroUnit
```

A hydropower generator, modelled as a `HydroUnit` node.

A hydropower generator is located between two [`HydroReservoir`](@ref)s or between a [`HydroReservoir`](@ref) and a `Sink` node corresponding to the ocean. It differs from a [`HydroGate`](@ref) as it allows for power generation desctibed through an [`AbstractPqCurve`](@ref).

## Fields

  * **`id`** is the name/identifier of the node.
  * **`cap::TimeProfile`** is the installed discharge or power capacity.
  * **`pq_curve::AbstractPqCurve` describes the relationship between power and discharge (water).
  * **`opex_var::TimeProfile`** is the variable operational costs per energy unit produced.
  * **`opex_fixed::TimeProfile`** is the fixed operational costs.
  * **`electricity_resource::Resource`** is the electricity resource generated as output.
  * **`water_resource::Resource`** is the water resource taken as input and discharged as output.
  * **`data::Vector{<:Data}`** is the additional data (*e.g.*, for investments or constraints through [`AbstractScheduleType`](@ref)). The field `data` is conditional through usage of a constructor.
