```julia
remove_time_series!(
    sys::PowerSystems.System,
    _::Type{T<:InfrastructureSystems.TimeSeriesData},
    component::PowerSystems.Component,
    name::String
)

```

コンポーネントと時系列タイプのための時系列データを削除します。
