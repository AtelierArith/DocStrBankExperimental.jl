```
Exemplar(;kw...)
```

Exemplars are example data points for aggregated data. Read [the specification](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/metrics/sdk.md#exemplar) to understand its relation to trace and metric.

## Keyword arguments:

  * `value`
  * `time_unix_nano`
  * `filtered_attributes`, extra attributes of a [`Measurement`](@ref) that are not included in a [`Metric`](@ref)'s `:attribute_keys` field.
  * `trace_id`, the `trace_id` in the span context when the measurement happens.
  * `span_id`, the `span_id` in the span context when the measurement happens.
