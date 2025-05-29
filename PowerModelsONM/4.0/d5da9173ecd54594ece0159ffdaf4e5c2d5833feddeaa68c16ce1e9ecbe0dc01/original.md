```
variable_storage_indicator(pm::AbstractUnbalancedPowerModel; nw::Int=nw_id_default, relax::Bool=false, report::Bool=true)
```

Variables for switching storage on/off $z^{strg}_i,~\forall i \in E$, binary if `relax=false`. Variables will appear in solution if `report=true`.
