```
struct PipeLinepackSimple <: PipeMode
```

Pipeline model with linepacking implemented as simple storage function.

# Fields

  * **`id::String`** is the identifier used in printed output.
  * **`inlet::Resource`** is the `Resource` going into transmission.
  * **`outlet::Resource`** is the `Resource` going out of the outlet of the transmission.
  * **`consuming::Resource`** is the `Resource` the transmission consumes by operating.
  * **`consumption_rate::TimeProfile`** the rate of which the resource `Pipeline.consuming` is consumed, as a ratio of the volume of the resource going into the inlet, *i.e.*:

    ```
      `consumption_rate` = consumed volume / inlet volume (per operational period)
    ```
  * **`trans_cap::Real`** is the capacity of the transmission mode.
  * **`trans_loss::Real`** is the loss of the transported resource during transmission, modelled as a ratio.
  * **`opex_var::TimeProfile`** is the variable operating expense per energy unit transported.
  * **`opex_fixed::TimeProfile`** is the fixed operating expense per installed capacity.
  * **`energy_share::Float64`** is the storage energy capacity relative to pipeline capacity.
  * **`data::Array{<:Data}`** is the additional data (*e.g.*, for investments). The field `data` is conditional through usage of a constructor.
