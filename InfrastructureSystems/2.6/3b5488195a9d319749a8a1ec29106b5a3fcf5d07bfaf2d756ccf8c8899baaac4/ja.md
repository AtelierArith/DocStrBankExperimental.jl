```julia
Probabilistic(
    name::AbstractString,
    series_data::InfrastructureSystems.RawTimeSeries,
    percentiles::Vector,
    resolution::Dates.Period;
    normalization_factor,
    scaling_factor_multiplier
) -> InfrastructureSystems.Probabilistic

```

RawTimeSeriesからDeterministicを構築します。
