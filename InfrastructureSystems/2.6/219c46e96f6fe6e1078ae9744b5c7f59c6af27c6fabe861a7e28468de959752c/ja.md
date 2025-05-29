```julia
get_next_time_series_array!(
    cache::InfrastructureSystems.TimeSeriesCache
) -> Any

```

次のTimeSeries.TimeArrayを返します。

すべてのデータが読み取られた場合は`nothing`を返します。再起動するには[`reset!`](@ref)を呼び出してください。開始時間を確認するには[`get_next_time`](@ref)を呼び出してください。

データがキャッシュに既に存在しない場合は、ストレージから読み取ります。

# 引数

  * `cache::StaticTimeSeriesCache`: キャッシュされたインスタンス

# 例

```julia
cache = ForecastCache(Deterministic, component, "max_active_power")
window1 = get_next_time_series_array!(cache)
window2 = get_next_time_series_array!(cache)
```
