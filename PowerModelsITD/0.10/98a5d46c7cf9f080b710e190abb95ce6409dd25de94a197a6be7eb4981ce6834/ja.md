```
function constraint_boundary_voltage_magnitude(
    pm::_PM.DCPPowerModel,
    pmd::_PMD.DCPUPowerModel,
    i::Int,
    f_idx::Tuple{Int,Int,Int},
    f_connections::Vector{Int},
    t_connections::Vector{Int};
    nw::Int = nw_id_default
)
```

DCP-DCPU 境界バス電圧の大きさの制約: DC はすべての vm = 1 を維持するため、空です。
