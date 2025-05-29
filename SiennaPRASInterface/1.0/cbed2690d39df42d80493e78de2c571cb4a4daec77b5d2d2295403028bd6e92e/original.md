```julia
generate_pras_system(
    sys::PowerSystems.System,
    aggregation::Type{AT<:PowerSystems.AggregationTopology}
) -> PRASCore.Systems.SystemModel{_A, _B, T, PRASCore.Systems.MW, PRASCore.Systems.MWh} where {_A, _B, T<:Dates.Period}
generate_pras_system(
    sys::PowerSystems.System,
    aggregation::Type{AT<:PowerSystems.AggregationTopology},
    lump_region_renewable_gens::Bool
) -> PRASCore.Systems.SystemModel{_A, _B, T, PRASCore.Systems.MW, PRASCore.Systems.MWh} where {_A, _B, T<:Dates.Period}
generate_pras_system(
    sys::PowerSystems.System,
    aggregation::Type{AT<:PowerSystems.AggregationTopology},
    lump_region_renewable_gens::Bool,
    export_location::Union{Nothing, String}
) -> PRASCore.Systems.SystemModel{_A, _B, T, PRASCore.Systems.MW, PRASCore.Systems.MWh} where {_A, _B, T<:Dates.Period}

```

Sienna/Data PowerSystems.jl System is the input and an object of PRAS SystemModel is returned. ...

# Arguments

  * `sys::PSY.System`: Sienna/Data PowerSystems.jl System
  * `aggregation<:PSY.AggregationTopology`: "PSY.Area" (or) "PSY.LoadZone" {Optional}
  * `lump_region_renewable_gens::Bool`: Whether to lumps PV and Wind generators in a region because usually these generators don't have FOR data {Optional}
  * `export_location::String`: Export location of the .pras file ...

# Returns

```
- `PRASCore.SystemModel`: PRAS SystemModel object
```

# Examples

```julia-repl
julia> generate_pras_system(psy_sys, PSY.Area)
PRAS SystemModel
```
