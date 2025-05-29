```
is_parameter_timeseries(x) = is_parameter_timeseries(typeof(x))
is_parameter_timeseries(::Type)
```

Get the parameter timeseries trait of a type. Defaults to [`NotTimeseries`](@ref) for all types. A type for which `is_parameter_timeseries(T) == Timeseries()` must also have `is_timeseries(T) == Timeseries()`.

See also: [`Timeseries`](@ref), [`NotTimeseries`](@ref), [`is_timeseries`](@ref).
