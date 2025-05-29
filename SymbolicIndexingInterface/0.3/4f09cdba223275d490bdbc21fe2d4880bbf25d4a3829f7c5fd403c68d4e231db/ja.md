```
is_timeseries(x) = is_timeseries(typeof(x))
is_timeseries(::Type)
```

型のタイムシリーズ特性を取得します。すべての型に対してデフォルトは [`NotTimeseries`](@ref) です。`is_timeseries(T) == Timeseries()` となる型は、パラメータタイムシリーズを持つ場合もあります。これは [`is_parameter_timeseries`](@ref) 特性によって決定されます。

関連情報: [`Timeseries`](@ref), [`NotTimeseries`](@ref), [`is_parameter_timeseries`](@ref).
