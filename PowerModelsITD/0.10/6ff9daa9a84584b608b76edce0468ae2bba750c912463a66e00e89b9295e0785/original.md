```
function constraint_boundary_voltage_magnitude(
    pm::_PM.AbstractSDPWRMModel,
    pmd::_PMD.SOCConicUBFPowerModel,
    i::Int,
    f_idx::Tuple{Int,Int,Int},
    f_connections::Vector{Int},
    t_connections::Vector{Int};
    nw::Int = nw_id_default
)
```

SDPWRM-SOCConicUBF boundary bus voltage magnitude (W variables) constraints.
