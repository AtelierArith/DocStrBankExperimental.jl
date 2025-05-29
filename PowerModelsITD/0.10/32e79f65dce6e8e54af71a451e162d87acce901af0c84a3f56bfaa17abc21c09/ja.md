```
function constraint_boundary_voltage_magnitude(
    pm::_PM.ACPPowerModel,
    pmd::_PMD.ACPUPowerModel,
    i::Int,
    f_idx::Tuple{Int,Int,Int},
    f_connections::Vector{Int},
    t_connections::Vector{Int};
    nw::Int = nw_id_default
)
```

ACP-ACPU境界バス電圧大きさ制約。
