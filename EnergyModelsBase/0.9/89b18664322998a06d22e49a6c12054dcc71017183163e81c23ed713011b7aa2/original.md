```
struct RefNetworkNode <: NetworkNode
```

A reference [`NetworkNode`](@ref) node. The `RefNetworkNode` utilizes a linear, time independent conversion rate of the `input` [`Resource`](@ref)s to the output [`Resource`](@ref)s, subject to the available capacity. The capacity is hereby normalized to a conversion value of 1 in the fields `input` and `output`.

# Fields

  * **`id`** is the name/identifier of the node.
  * **`cap::TimeProfile`** is the installed capacity.
  * **`opex_var::TimeProfile`** is the variable operating expense per per capacity usage through the variable `:cap_use`.
  * **`opex_fixed::TimeProfile`** is the fixed operating expense per installed capacity through the variable `:cap_inst`.
  * **`input::Dict{<:Resource,<:Real}`** are the input [`Resource`](@ref)s with conversion value `Real`.
  * **`output::Dict{<:Resource,<:Real}`** are the generated [`Resource`](@ref)s with conversion value `Real`.
  * **`data::Vector{Data}`** is the additional data (*e.g.*, for investments). The field `data` is conditional through usage of a constructor.
