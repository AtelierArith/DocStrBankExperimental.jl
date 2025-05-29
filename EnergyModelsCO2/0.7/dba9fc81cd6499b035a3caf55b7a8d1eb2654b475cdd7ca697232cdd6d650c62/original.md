```
RefNetworkNodeRetrofit <: NetworkNodeWithRetrofit
```

This node allows for retrofitting CO₂ capture to a `NetworkNode`.

It corresponds to a [`RefNetworkNode`](@extref EnergyModelsBase.RefNetworkNode) node in which the CO₂ is not emitted. Instead, it is transferred to a `co2_proxy` that is fed subsequently to a node ([`CCSRetroFit`](@ref)) in which it is either captured, or emitted.

The `co2_proxy` does not have to be specified as `output` resource.

# Fields

  * **`id`** is the name/identifier of the node.
  * **`cap::TimeProfile`** is the installed capacity.
  * **`opex_var::TimeProfile`** is the variational operational costs per energy unit produced.
  * **`opex_fixed::TimeProfile`** is the fixed operational costs.
  * **`input::Dict{<:Resource, <:Real}`** are the input `Resource`s with conversion value `Real`.
  * **`output::Dict{<:Resource, <:Real}`** are the generated `Resource`s with conversion value `Real`. `co2_proxy` is required to be included to be available to have CO₂ capture applied properly.
  * **`co2_proxy::Resource`** is the instance of the `Resource` used for calculating internally the CO₂ flow from the `RefNetworkNodeRetrofit` to the `CCSRetroFit` node.
  * **`data::Array{<:Data}`** is the additional data (e.g. for investments).
