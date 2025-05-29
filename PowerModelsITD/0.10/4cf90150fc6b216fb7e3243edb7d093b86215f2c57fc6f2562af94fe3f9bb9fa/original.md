```
function constraint_boundary_voltage_angle(
    pm::_PM.AbstractSOCWRConicModel,
    pmd::_PMD.SOCConicUBFPowerModel,
    i::Int,
    f_idx::Tuple{Int,Int,Int},
    f_connections::Vector{Int},
    t_connections::Vector{Int};
    nw::Int = nw_id_default
)
```

SOCWRConic-SOCConicUBF boundary bus voltage angle constraints.
