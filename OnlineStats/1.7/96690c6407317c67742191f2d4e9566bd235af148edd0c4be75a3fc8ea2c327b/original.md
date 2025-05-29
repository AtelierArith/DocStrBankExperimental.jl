```
MovingTimeWindow{T<:TimeType, S}(window::Dates.Period)
MovingTimeWindow(window::Dates.Period; valtype=Float64, timetype=Date)
```

Fit a moving window of data based on time stamps.  Each observation must be a `Tuple`, `NamedTuple`, or `Pair` where the first item is `<: Dates.TimeType`.  Observations with a `timestamp` NOT in the range

```
now() - window ≤ timestamp ≤ now()
```

are discarded on every `fit!`.

# Example

```
using Dates
dts = Date(2010):Day(1):Date(2011)
y = rand(length(dts))

o = MovingTimeWindow(Day(4); timetype=Date, valtype=Float64)
fit!(o, zip(dts, y))
```
