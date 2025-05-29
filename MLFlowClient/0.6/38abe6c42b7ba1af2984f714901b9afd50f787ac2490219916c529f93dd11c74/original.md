```
getrun(instance::MLFlow, run_id::String)
```

Get metadata, metrics, params, and tags for a [`Run`](@ref). In the case where multiple metrics with the same key are logged for a [`Run`](@ref), return only the value with the latest timestamp. If there are multiple values with the latest timestamp, return the maximum of these values.

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `run_id`: ID of the [`Run`](@ref) to fetch.

# Returns

An instance of type [`Run`](@ref).
