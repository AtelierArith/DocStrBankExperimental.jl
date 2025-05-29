```
function constraint_boundary_voltage_magnitude(
    pm::_PM.DCPPowerModel,
    pmd::_PMD.DCPUPowerModel,
    i::Int,
    f_idx::Tuple{Int,Int,Int},
    f_connections::Vector{Int},
    t_connections::Vector{Int};
    nw::Int = nw_id_default
)
```

DCP-DCPU boundary bus voltage magnitude constraints: empty since DC keeps vm = 1 for all.
