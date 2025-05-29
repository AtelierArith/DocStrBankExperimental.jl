```
function constraint_transmission_power_balance(
    pmitd::AbstractPowerModelITD,
    pm::_PM.AbstractACRModel,
    n::Int,
    i::Int,
    bus_arcs,
    bus_arcs_dc,
    bus_arcs_sw,
    bus_gens,
    bus_storage,
    bus_pd,
    bus_qd,
    bus_gs,
    bus_bs,
    bus_arcs_boundary_from
)
```

ACR送電制約電力バランス。
