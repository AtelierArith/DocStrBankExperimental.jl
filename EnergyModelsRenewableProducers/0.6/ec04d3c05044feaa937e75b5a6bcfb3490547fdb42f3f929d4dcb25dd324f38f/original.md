```
HydroPump <: HydroUnit
```

A hydropower pump, modelled as a `HydroUnit` node.

A hydropower pump is located between two [`HydroReservoir`](@ref)s and allows the transfer of water from one reservoir to the other through pumping the water.

## Fields

  * **`id`** is the name/identifier of the node.
  * **`cap::TimeProfile`** is the installed pumping capacity in piwer or volume per time unit.
  * **`pq_curve::AbstractPqCurve` describes the relationship between power and pumping of water.
  * **`opex_var::TimeProfile`** is the variable operational costs per energy unit produced.
  * **`opex_fixed::TimeProfile`** is the fixed operational costs.
  * **`electricity_resource::Resource`** is the electricity resource taken as input (consumed).
  * **`water_resource::Resource`** is the water resource taken as input and discharged (pumped) as output.
  * **`data::Vector{<:Data}`** is the additional data (*e.g.*, for investments or constraints through [`AbstractScheduleType`](@ref)). The field `data` is conditional through usage of a constructor.
