```
struct Timeseries <: IsTimeseriesTrait end
```

時系列データを含む型を示すトレイトです。これは、[`state_values`](@ref)や[`current_time`](@ref)などの関数の動作に影響を与えます。

関連情報: [`NotTimeseries`](@ref), [`is_timeseries`](@ref)
