```
function constraint_boundary_voltage_angle(
    pm::_PM.AbstractSDPWRMModel,
    pmd::_PMD.SOCConicUBFPowerModel,
    i::Int,
    f_idx::Tuple{Int,Int,Int},
    f_connections::Vector{Int},
    t_connections::Vector{Int};
    nw::Int = nw_id_default
)
```

SDPWRM-SOCConicUBF 境界バス電圧角度制約。
