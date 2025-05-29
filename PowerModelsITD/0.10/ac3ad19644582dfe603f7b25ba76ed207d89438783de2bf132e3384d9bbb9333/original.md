```
function constraint_boundary_voltage_magnitude(
    pm::_PM.NFAPowerModel,
    pmd::_PMD.NFAUPowerModel,
    i::Int,
    f_idx::Tuple{Int,Int,Int},
    f_connections::Vector{Int},
    t_connections::Vector{Int};
    nw::Int = nw_id_default
)
```

NFA-NFAU boundary bus voltage magnitude constraints: empty NFA.
