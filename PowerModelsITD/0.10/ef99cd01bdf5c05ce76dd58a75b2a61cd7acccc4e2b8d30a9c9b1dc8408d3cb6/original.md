```
function constraint_boundary_voltage_magnitude(
    pm::_PM.AbstractSOCBFModel,
    pmd::_PMD.LPUBFDiagPowerModel,
    i::Int,
    f_idx::Tuple{Int,Int,Int},
    f_connections::Vector{Int},
    t_connections::Vector{Int};
    nw::Int=nw_id_default
)
```

SOCBF-LinDist3FlowPowerModel boundary bus voltage magnitude constraints.
