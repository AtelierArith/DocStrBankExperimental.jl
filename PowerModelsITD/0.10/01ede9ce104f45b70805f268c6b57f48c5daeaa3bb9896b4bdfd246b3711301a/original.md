```
function constraint_boundary_voltage_angle(
    pm::_PM.ACRPowerModel,
    pmd::_PMD.ACRUPowerModel,
    i::Int,
    f_idx::Tuple{Int,Int,Int},
    f_connections::Vector{Int},
    t_connections::Vector{Int};
    nw::Int = nw_id_default
)
```

ACR-ACRU boundary bus voltage angle constraints.
