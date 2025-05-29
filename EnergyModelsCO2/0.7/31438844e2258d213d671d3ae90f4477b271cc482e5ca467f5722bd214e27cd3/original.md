```
CO2Source <: Source
```

A CO₂ `Source` node. Its only difference from a [`RefSource`](@extref EnergyModelsBase.RefSource) is that is allows for CO₂ as outlet.

# Fields

  * **`id`** is the name/identifier of the node.
  * **`cap::TimeProfile`** is the installed capacity.
  * **`opex_var::TimeProfile`** is the variational operational costs per energy unit produced.
  * **`opex_fixed::TimeProfile`** is the fixed operational costs.
  * **`output::Dict{<:Resource, <:Real}`** are the generated `Resource`s with conversion value `Real`.
  * **`data::Array{<:Data}`** is the additional data (e.g. for investments). The field `data` is conditional through usage of a constructor.
