```
HeatPump <: EMB.NetworkNode
```

A `HeatPump` node to convert low temperature heat to high(er) temperature heat by utilizing an exergy driving force (*e.g.*, electricity).

# Fields

  * **`id`** is the name/identifier of the node.
  * **`cap::TimeProfile`** is the installed heating capacity.
  * **`cap_lower_bound`** is the lower capacity bound for flexibility within [0, 1] reflecting the lowest possible relative capacity use.
  * **`t_source`** is the temperature profile of the heat source
  * **`t_sink`** is the sink temperature of the condensator. The temperature must be given in °C.
  * **`eff_carnot`** is the Carnot Efficiency COP*real/COP*carnot. The value must be within [0, 1].
  * **`input_heat`** is the resource for the low temperature heat input.
  * **`driving_force`** is the resource of the driving force, *e.g.*, electricity.
  * **`opex_var::TimeProfile`** is the variable operating expense per energy unit produced.
  * **`opex_fixed::TimeProfile`** is the fixed operating expense.
  * **`output::Dict{<:Resource, <:Real}`** are the produced [`Resource`](@extref EnergyModelsBase.Resource)s with conversion value `Real`.
  * **`data::Vector{<:Data}`** is the additional data (*e.g.*, for investments). The field `data` is conditional through usage of a constructor.
