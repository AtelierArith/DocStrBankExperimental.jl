```
function constraint_boundary_voltage_magnitude(
    pm::_PM.AbstractBFAModel,
    pmd::_PMD.LPUBFDiagPowerModel,
    i::Int,
    f_idx::Tuple{Int,Int,Int},
    f_connections::Vector{Int},
    t_connections::Vector{Int};
    nw::Int=nw_id_default
)
```

BFA-LinDist3FlowPowerModel 境界バス電圧の大きさの制約。
