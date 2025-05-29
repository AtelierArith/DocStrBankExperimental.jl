```
function constraint_boundary_voltage_angle(
    pm::_PM.AbstractSOCBFModel,
    pmd::_PMD.LPUBFDiagPowerModel,
    i::Int,
    f_idx::Tuple{Int,Int,Int},
    f_connections::Vector{Int},
    t_connections::Vector{Int};
    nw::Int=nw_id_default
)
```

SOCBF-LinDist3FlowPowerModel 境界バス電圧角度制約。
