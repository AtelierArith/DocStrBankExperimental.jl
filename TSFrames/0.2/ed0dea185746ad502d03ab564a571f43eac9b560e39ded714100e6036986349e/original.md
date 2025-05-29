### Frequency conversion

Set of convenience methods for frequency conversion of `TimeType` index types. Internally, they call `endpoints()` to do the actual conversion. `n` is the number of periods of the `period` type. For example, `to_monthly(tsf, 2)` will resample the time series to "every 2 months".

```julia
to_period(tsf::TSFrame, period::T)::TSFrame where {T<:Period}
to_yearly(tsf::TSFrame, n=1)::TSFrame
to_quarterly(tsf::TSFrame, n=1)::TSFrame
to_monthly(tsf::TSFrame, n=1)::TSFrame
to_weekly(tsf::TSFrame, n=1)::TSFrame
to_daily(tsf::TSFrame, n=1)::TSFrame
to_hourly(tsf::TSFrame, n=1)::TSFrame
to_minutes(tsf::TSFrame, n=1)::TSFrame
to_seconds(tsf::TSFrame, n=1)::TSFrame
to_milliseconds(tsf::TSFrame, n=1)::TSFrame
to_microseconds(tsf::TSFrame, n=1)::TSFrame
to_nanoseconds(tsf::TSFrame, n=1)::TSFrame
```
