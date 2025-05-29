```
variable_generator_indicator(pm::AbstractUnbalancedPowerModel; nw::Int=nw_id_default, relax::Bool=false, report::Bool=true)
```

Variables for switching generators on/off $z^{gen}_i,~\forall i \in G$, binary if `relax=false`. Variables will appear in solution if `report=true`.
