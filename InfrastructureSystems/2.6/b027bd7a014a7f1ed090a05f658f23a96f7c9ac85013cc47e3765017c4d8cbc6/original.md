```julia
has_time_series(
    val::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    _::Type{T<:InfrastructureSystems.TimeSeriesData}
) -> Bool

```

Return true if the component or supplemental attribute has time series data of type T.
