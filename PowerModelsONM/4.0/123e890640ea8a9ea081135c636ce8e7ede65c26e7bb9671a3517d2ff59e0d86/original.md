```
variable_inverter_indicator(pm::AbstractUnbalancedPowerModel; nw::Int=nw_id_default, relax::Bool=false, report::Bool=true)
```

Variables for indicating whether a DER (storage or gen) is in grid-forming mode (1) or grid-following mode (0), binary is `relax=false`. Variables will appear in solution if `report=true`. If "inverter"==GRID_FOLLOWING on the device, the inverter variable will be a constant.
