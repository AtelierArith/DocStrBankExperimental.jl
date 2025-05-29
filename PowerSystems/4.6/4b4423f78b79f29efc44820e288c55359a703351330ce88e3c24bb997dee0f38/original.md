```julia
get_start_up(
    value::PowerSystems.ThermalGenerationCost
) -> Union{Float64, @NamedTuple{hot::Float64, warm::Float64, cold::Float64}}

```

Get [`ThermalGenerationCost`](@ref) `start_up`.
