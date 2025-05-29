```
InterfaceLimit(;file)
```

Constrain power flowing between regions for each representative hour. See [`summarize_table(::Val{:interface_limit})`](@ref).

  * [`modify_raw_data!(mod::InterfaceLimit, config, data)`](@ref)
  * [`modify_model!(mod::InterfaceLimit, config, data, model)`](@ref)

To change the power flow min/max for each year and/or hour, see [`AdjustYearly`](@ref) and [`AdjustHourly`](@ref).
