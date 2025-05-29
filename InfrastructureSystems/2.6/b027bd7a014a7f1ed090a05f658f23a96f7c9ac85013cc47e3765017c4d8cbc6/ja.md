```julia
has_time_series(
    val::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    _::Type{T<:InfrastructureSystems.TimeSeriesData}
) -> Bool

```

コンポーネントまたは補足属性がタイプ T の時系列データを持っている場合は true を返します。
