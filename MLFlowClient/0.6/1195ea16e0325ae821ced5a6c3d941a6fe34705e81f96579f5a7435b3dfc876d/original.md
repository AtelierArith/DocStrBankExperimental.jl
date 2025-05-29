```
Metric <: LoggingData
```

Metric associated with a run, represented as a key-value pair.

# Fields

  * `key::String`: Key identifying this metric.
  * `value::Float64`: Value associated with this metric.
  * `timestamp::Int64`: The timestamp at which this metric was recorded.
  * `step::Union{Int64, Nothing}`: Step at which to log the metric.
