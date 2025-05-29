```
function constraint_boundary_voltage_magnitude(
    pm::_PM.ACRPowerModel,
    pmd::_PMD.FBSUBFPowerModel,
    i::Int,
    f_idx::Tuple{Int,Int,Int},
    f_connections::Vector{Int},
    t_connections::Vector{Int};
    nw::Int=nw_id_default
)
```

ACR-FBSU boundary bus voltage magnitude constraints.
