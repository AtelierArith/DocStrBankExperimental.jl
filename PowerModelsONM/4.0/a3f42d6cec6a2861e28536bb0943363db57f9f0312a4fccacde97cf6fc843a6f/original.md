```
variable_bus_voltage_indicator(
    pm::AbstractUnbalancedPowerModel;
    nw::Int=nw_id_default,
    relax::Bool=false,
    report::Bool=true
)
```

Variables for switching buses on/off $z^{bus}_i,~\forall i \in N$, binary if `relax=false`. Variables will appear in solution if `report=true`.
