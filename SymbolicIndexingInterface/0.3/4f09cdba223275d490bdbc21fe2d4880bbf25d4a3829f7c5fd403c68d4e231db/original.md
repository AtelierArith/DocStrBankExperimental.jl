```
is_timeseries(x) = is_timeseries(typeof(x))
is_timeseries(::Type)
```

Get the timeseries trait of a type. Defaults to [`NotTimeseries`](@ref) for all types. A type for which `is_timeseries(T) == Timeseries()` may also have a parameter timeseries. This is determined by the [`is_parameter_timeseries`](@ref) trait.

See also: [`Timeseries`](@ref), [`NotTimeseries`](@ref), [`is_parameter_timeseries`](@ref).
