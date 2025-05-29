```
CCSRetroFit <: Network
```

This node allows for investments into CO₂ capture retrofit to a [`RefNetworkNodeRetrofit`](@ref) node. The capture process is implemented through the variable `:cap_use`

The `co2_proxy` does not have to be specified as `input` resource.

# Fields

  * **`id`** is the name/identifier of the node.
  * **`cap::TimeProfile`** is the installed capacity.
  * **`opex_var::TimeProfile`** is the variational operational costs per unit CO2 captured.
  * **`opex_fixed::TimeProfile`** is the fixed operational costs.
  * **`input::Dict{<:Resource, <:Real}`** are the input `Resource`s with conversion value `Real`.
  * **`output::Dict{<:Resource, <:Real}`** are the generated `Resource`s with conversion value `Real`. The CO₂ instance is required to be included to be available to have CO₂ capture applied properly.
  * **`co2_proxy::Resource`** is the instance of the `Resource` used for calculating internally the CO₂ flow from the `RefNetworkNodeRetrofit` to the `CCSRetroFit` node.
  * **`data::Array{<:Data}`** is the additional data (e.g. for investments).
