```julia
Deterministic(
    name::AbstractString,
    series_data::InfrastructureSystems.RawTimeSeries,
    resolution::Dates.Period;
    normalization_factor,
    scaling_factor_multiplier
) -> InfrastructureSystems.Deterministic

```

RawTimeSeriesからDeterministicを構築します。
