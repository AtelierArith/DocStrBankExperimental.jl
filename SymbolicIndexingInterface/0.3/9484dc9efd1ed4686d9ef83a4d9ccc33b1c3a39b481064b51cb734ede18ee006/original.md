```
struct Timeseries <: IsTimeseriesTrait end
```

Trait indicating a type contains timeseries data. This affects the behaviour of functions such as [`state_values`](@ref) and [`current_time`](@ref).

See also: [`NotTimeseries`](@ref), [`is_timeseries`](@ref)
