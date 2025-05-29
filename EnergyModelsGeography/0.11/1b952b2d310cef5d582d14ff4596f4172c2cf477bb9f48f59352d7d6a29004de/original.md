```
LimitedExchangeArea <: Area
```

A `LimitedExchangeArea` is an area in which the export is limited in each individual operational period for the provided resources. This can be necessary when an area is coupled with multiple other areas and the total export capacity should be restricted.

# Fields

  * **`id`** is the name/identifier of the area.
  * **`name`** is the name of the area.
  * **`lon::Real`** is the longitudinal position of the area.
  * **`lat::Real`** is the latitudinal position of the area.
  * **`node::Availability`** is the `Availability` node routing different resources within an area.
  * **`limit::Dict{<:EMB.Resource, <:TimeProfile}`** is the amount of a resource that can be exchanged with other areas.
