```
variable_load_indicator(pm::AbstractUnbalancedPowerModel; nw::Int=nw_id_default, relax::Bool=false, report::Bool=true)
```

Variables for switching loads on/off $z^{d}_i,~\forall i \in L$, binary if `relax=false`. Variables will appear in solution if `report=true`.
