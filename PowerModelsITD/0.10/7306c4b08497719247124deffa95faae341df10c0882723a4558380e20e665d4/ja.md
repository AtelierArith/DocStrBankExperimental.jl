```
function constraint_boundary_voltage_magnitude(
    pm::_PM.AbstractSOCWRConicModel,
    pmd::_PMD.SOCConicUBFPowerModel,
    i::Int,
    f_idx::Tuple{Int,Int,Int},
    f_connections::Vector{Int},
    t_connections::Vector{Int};
    nw::Int = nw_id_default
)
```

SOCWRConic-SOCConicUBF 境界バス電圧の大きさ (W 変数) 制約。
