```julia
bulk_add_time_series!(
    sys::PowerSystems.System,
    associations;
    batch_size
) -> Vector{InfrastructureSystems.TimeSeriesKey}

```

時系列を一括で追加します。

[`begin_time_series_update`](@ref) の使用を推奨します。

# 例

```julia
# `read_time_series` が、発電機名に基づいて決定論的予測に適したデータを返すことを前提としています
# ファイル名がコンポーネントと時系列名に一致します。
resolution = Dates.Hour(1)
associations = (
    IS.TimeSeriesAssociation(
        gen,
        Deterministic(
            data = read_time_series(get_name(gen) * ".csv"),
            name = "get_max_active_power",
            resolution=resolution),
    )
    for gen in get_components(ThermalStandard, sys)
)
bulk_add_time_series!(sys, associations)
```
