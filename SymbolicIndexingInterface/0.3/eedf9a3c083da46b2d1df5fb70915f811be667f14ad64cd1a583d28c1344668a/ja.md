```
struct NotTimeseries <: IsTimeseriesTrait end
```

時系列データを含まない型を示すトレイトです。これは、[`state_values`](@ref)や[`current_time`](@ref)などの関数の動作に影響を与えます。型が`NotTimeseries`である場合、これはその型が時系列データを*保存*していないことを意味するだけです。それは依然として時間依存である可能性があります。たとえば、`ODEProblem`はシステムの初期状態のみを保存するため、`NotTimeseries`ですが、依然として時間依存です。これはすべての型のデフォルトのトレイトバリアントです。

関連情報: [`Timeseries`](@ref), [`is_timeseries`](@ref)。
