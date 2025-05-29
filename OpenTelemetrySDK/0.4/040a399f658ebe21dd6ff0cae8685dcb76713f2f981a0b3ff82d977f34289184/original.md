```
View(name=nothing;kwargs...)
```

The `name` support wildcard.

See more details in [the specification](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/metrics/sdk.md#view).

## Keyword arguments

  * `description = nothing`,
  * `attribute_keys = nothing`,
  * `extra_dimensions = BoundedAttributes()`,
  * `aggregation = nothing`,
  * `instrument_name = nothing`,
  * `instrument_type = nothing`,
  * `meter_name = nothing`,
  * `meter_version = nothing`,
  * `meter_schema_url = nothing`,
