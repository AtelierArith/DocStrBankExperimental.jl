```
function constraint_boundary_voltage_magnitude(
    pm::_PM.AbstractSOCBFModel,
    pmd::_PMD.SOCNLPUBFPowerModel,
    i::Int,
    f_idx::Tuple{Int,Int,Int},
    f_connections::Vector{Int},
    t_connections::Vector{Int};
    nw::Int = nw_id_default
)
```

SOCBF-SOCNLUBF boundary bus voltage magnitude (W variables) constraints.
