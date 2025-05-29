```
logmetric(instance::MLFlow, run_id::String, key::String, value::Float64;
    timestamp::Int64=round(Int, now() |> datetime2unix),
    step::Union{Int64, Missing}=missing)
logmetric(instance::MLFlow, run::Run, key::String, value::Float64;
    timestamp::Int64=round(Int, now() |> datetime2unix),
    step::Union{Int64, Missing}=missing)
```

Log a [`Metric`](@ref) for a [`Run`](@ref). A [`Metric`](@ref) is a key-value pair (string key, float value) with an associated timestamp. Examples include the various metrics that represent ML model accuracy. A [`Metric`](@ref) can be logged multiple times.

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `run_id`: ID of the [`Run`](@ref) under which to log the [`Metric`](@ref).
  * `key`: Name of the [`Metric`](@ref).
  * `value`: Double value of the [`Metric`](@ref) being logged.
  * `timestamp`: Unix timestamp in milliseconds at the time [`Metric`](@ref) was logged.
  * `step`: Step at which to log the [`Metric`](@ref).

# Returns

`true` if successful. Otherwise, raises exception.
