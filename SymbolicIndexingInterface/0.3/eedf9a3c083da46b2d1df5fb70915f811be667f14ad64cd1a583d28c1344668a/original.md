```
struct NotTimeseries <: IsTimeseriesTrait end
```

Trait indicating a type does not contain timeseries data. This affects the behaviour of functions such as [`state_values`](@ref) and [`current_time`](@ref). Note that if a type is `NotTimeseries` this only implies that it does not *store* timeseries data. It may still be time-dependent. For example, an `ODEProblem` only stores the initial state of a system, so it is `NotTimeseries`, but still time-dependent. This is the default trait variant for all types.

See also: [`Timeseries`](@ref), [`is_timeseries`](@ref).
