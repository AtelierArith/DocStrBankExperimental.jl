```
parse_metric_bindings(df::DataFrame) -> Vector{MetricBinding}
```

Parse a `DataFrame` with metric‑binding definitions and return a vector of [`MetricBinding`](@ref) objects.

The DataFrame should contain the following columns:

  * `id`: Unique identifier for the metric binding.
  * `scenario`: The scenario to which the metric binding applies.
  * `endpoint`: The observable (endpoint) associated with the metric binding.
  * `active`: (optional) A boolean indicating whether the metric binding is active (default is `true`).
  * `metric.type`: The type of metric (e.g., "mean", "category", etc.).
  * `metric.<parameter>`: Additional parameters for the metric, depending on its type.

The function uses the `PARSERS` dictionary to find the appropriate parser for the metric type. The function iterates over each row of the DataFrame, extracting the relevant information and creating a `MetricBinding` object.
