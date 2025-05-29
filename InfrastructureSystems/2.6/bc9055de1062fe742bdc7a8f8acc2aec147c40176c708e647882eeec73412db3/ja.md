```julia
get_next_time(
    cache::InfrastructureSystems.TimeSeriesCache
) -> Any

```

[`get_next_time_series_array!`](@ref)を使用して次の読み取りのタイムスタンプを返します。

すべてのデータが読み取られた場合は`nothing`を返します。
