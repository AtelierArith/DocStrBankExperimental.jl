```
GeoAvailability <: EMB.Availability
```

A geography `Availability` node for substituion of the general [`GenAvailability`](@extref EnergyModelsBase.GenAvailability) node. A `GeoAvailability` is required if transmission should be included between individual [`Area`](@refs due to a changed mass balance.

# Fields

  * **`id`** is the name/identifier of the node.
  * **`inputs::Vector{<:Resource}`** are the input [`Resource`](@extref EnergyModelsBase.Resource)s.
  * **`output::Vector{<:Resource}`** are the output [`Resource`](@extref EnergyModelsBase.Resource)s.
