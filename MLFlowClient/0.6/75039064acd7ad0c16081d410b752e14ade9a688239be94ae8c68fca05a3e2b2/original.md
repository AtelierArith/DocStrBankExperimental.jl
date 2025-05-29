```
logparam(instance::MLFlow, run_id::String, key::String, value::String)
logparam(instance::MLFlow, run::Run, key::String, value::String)
logparam(instance::MLFlow, run_id::String, param::Param)
logparam(instance::MLFlow, run::Run, param::Param)
```

Log a [`Param`](@ref) used for a [`Run`](@ref). A [`Param`](@ref) is a key-value pair (string key, string value). Examples include hyperparameters used for ML model training and constant dates and values used in an ETL pipeline. A [`Param`](@ref) can be logged only once for a [`Run`](@ref).

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `run_id`: ID of the [`Run`](@ref) under which to log the [`Param`](@ref).
  * `key`: Name of the [`Param`](@ref).
  * `value`: String value of the [`Param`](@ref) being logged.

# Returns

`true` if successful. Otherwise, raises exception.
