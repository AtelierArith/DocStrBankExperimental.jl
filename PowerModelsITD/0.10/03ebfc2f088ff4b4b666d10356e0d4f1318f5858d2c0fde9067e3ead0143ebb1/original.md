```
function constraint_boundary_voltage_angle(
    pm::_PM.ACRPowerModel,
    pmd::_PMD.FOTRUPowerModel,
    i::Int,
    f_idx::Tuple{Int,Int,Int},
    f_connections::Vector{Int},
    t_connections::Vector{Int};
    nw::Int=nw_id_default
)
```

ACR-FOTRU boundary bus voltage angle constraints.
