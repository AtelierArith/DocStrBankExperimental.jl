```
time_from_index(sample_rate, sample_range::AbstractUnitRange)
```

Return the `TimeSpan` corresponding to `sample_range` given `sample_rate` in Hz.

Note that the returned span includes the time period between the final sample and its successor, excluding the successor itself.

Examples:

```jldoctest
julia> time_from_index(100, 1:100)
TimeSpan(0 nanoseconds, 1000000000 nanoseconds)

julia> time_from_index(100, 101:101)
TimeSpan(1000000000 nanoseconds, 1000000001 nanoseconds)

julia> time_from_index(100, 301:600)
TimeSpan(3000000000 nanoseconds, 6000000000 nanoseconds)
```
