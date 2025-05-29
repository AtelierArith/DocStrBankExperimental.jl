```
function constraint_transmission_current_balance(
    pmitd::AbstractPowerModelITD,
    pm::_PM.AbstractIVRModel,
    n::Int,
    i::Int,
    bus_arcs,
    bus_arcs_dc,
    bus_gens,
    bus_pd,
    bus_qd,
    bus_gs,
    bus_bs,
    bus_arcs_boundary_from
)
```

IVR transmission constraint power balance.
