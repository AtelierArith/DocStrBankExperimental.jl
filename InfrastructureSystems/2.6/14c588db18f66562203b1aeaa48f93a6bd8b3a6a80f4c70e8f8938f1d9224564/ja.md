```julia
get_time_series_keys(
    store::InfrastructureSystems.TimeSeriesMetadataStore,
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute}
) -> Vector

```

所有者に添付された各時系列配列に関する情報を返します。この情報は `get_time_series` を呼び出すために使用できます。
