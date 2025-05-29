```julia
get_start_up(
    value::PowerSystems.ThermalGenerationCost
) -> Union{Float64, @NamedTuple{hot::Float64, warm::Float64, cold::Float64}}

```

[`ThermalGenerationCost`](@ref) の `start_up` を取得します。
