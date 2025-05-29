```
HeatExchanger
```

A `HeatExchanger` node to convert "raw" surplus energy from other processes to "available" energy that can be used in the District Heating network.

The default heat exchanger assumes that mass flows can be different to optimize heat transfer. This is encoded by the type parameter `HeatExchangerAssumptions`. The default value is `DifferentMassFlows`, the alternative is to specify `EqualMassFlows` to limit heat exchange to equal mass flow in the two circuits.

# Fields

  * **`id`** is the name/identifier of the node.
  * **`cap::TimeProfile`** is the installed capacity.
  * **`opex_var::TimeProfile`** is the variable operating expense per energy unit produced.
  * **`opex_fixed::TimeProfile`** is the fixed operating expense.
  * **`input::Dict{<:Resource, <:Real}`** are the input `Resource`s with conversion value `Real`.
  * **`output::Dict{<:Resource, <:Real}`** are the generated `Resource`s with conversion value `Real`.
  * **`data::Vector{Data}`** is the additional data (e.g. for investments). The field `data` is conditional through usage of a constructor.
  * **`delta_t_min`** is the ΔT_min for the heat exchanger
