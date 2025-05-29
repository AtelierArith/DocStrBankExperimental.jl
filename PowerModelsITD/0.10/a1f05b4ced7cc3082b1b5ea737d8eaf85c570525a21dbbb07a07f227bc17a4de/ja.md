```
function constraint_distribution_power_balance(
    pmitd::AbstractPowerModelITD,
    pmd::_PMD.AbstractUnbalancedWModels,
    n::Int,
    i::Int,
    terminals::Vector{Int},
    grounded::Vector{Bool},
    bus_arcs::Vector{Tuple{Tuple{Int,Int,Int},Vector{Int}}},
    bus_arcs_sw::Vector{Tuple{Tuple{Int,Int,Int},Vector{Int}}},
    bus_arcs_trans::Vector{Tuple{Tuple{Int,Int,Int},Vector{Int}}},
    bus_gens::Vector{Tuple{Int,Vector{Int}}},
    bus_storage::Vector{Tuple{Int,Vector{Int}}},
    bus_loads::Vector{Tuple{Int,Vector{Int}}},
    bus_shunts::Vector{Tuple{Int,Vector{Int}}},
    bus_arcs_boundary_to
)
```

不均衡Wモデルの分配制約電力バランス。
