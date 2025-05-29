```julia
get_time_series_keys(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute}
) -> Vector

```

オーナーに付随する各時系列配列に関する情報を返します。この情報は、[`get_time_series(::TimeSeriesOwners, ::TimeSeriesKey)`](@ref)を呼び出すために使用できます。
