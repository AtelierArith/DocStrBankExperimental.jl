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

Sienna/Data PowerSystems.jl システムが入力され、PRAS SystemModel のオブジェクトが返されます。 ...

# 引数

  * `sys::PSY.System`: Sienna/Data PowerSystems.jl システム
  * `aggregation<:PSY.AggregationTopology`: "PSY.Area"（または）"PSY.LoadZone" {オプション}
  * `lump_region_renewable_gens::Bool`: 通常、これらの発電機には FOR データがないため、地域内の PV および風力発電機をまとめるかどうか {オプション}
  * `export_location::String`: .pras ファイルのエクスポート先 ...

# 戻り値

```
- `PRASCore.SystemModel`: PRAS SystemModel オブジェクト
```

# 例

```julia-repl
julia> generate_pras_system(psy_sys, PSY.Area)
PRAS SystemModel
```
