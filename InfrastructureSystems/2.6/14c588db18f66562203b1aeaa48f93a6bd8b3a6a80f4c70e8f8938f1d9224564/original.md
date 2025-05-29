```julia
get_time_series_keys(
    store::InfrastructureSystems.TimeSeriesMetadataStore,
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute}
) -> Vector

```

Return information about each time series array attached to the owner. This information can be used to call `get_time_series`.
