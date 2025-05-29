```
is_parameter_timeseries(x) = is_parameter_timeseries(typeof(x))
is_parameter_timeseries(::Type)
```

型のパラメータ時系列特性を取得します。すべての型に対してデフォルトは [`NotTimeseries`](@ref) です。`is_parameter_timeseries(T) == Timeseries()` である型は、`is_timeseries(T) == Timeseries()` でもある必要があります。

関連情報: [`Timeseries`](@ref), [`NotTimeseries`](@ref), [`is_timeseries`](@ref).
