```
function constraint_boundary_voltage_angle(
    pm::_PM.DCPPowerModel,
    pmd::_PMD.DCPUPowerModel,
    i::Int,
    f_idx::Tuple{Int,Int,Int},
    f_connections::Vector{Int},
    t_connections::Vector{Int};
    nw::Int = nw_id_default
)
```

DCP-DCPU境界バス電圧角度制約: DCP角度。
