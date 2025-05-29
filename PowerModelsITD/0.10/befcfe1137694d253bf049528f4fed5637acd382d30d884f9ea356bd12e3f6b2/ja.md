```
function constraint_boundary_voltage_angle(
    pm::_PM.NFAPowerModel,
    pmd::_PMD.NFAUPowerModel,
    i::Int,
    f_idx::Tuple{Int,Int,Int},
    f_connections::Vector{Int},
    t_connections::Vector{Int};
    nw::Int = nw_id_default
)
```

NFA-NFAU境界バス電圧角度制約: 空のNFA角度。
