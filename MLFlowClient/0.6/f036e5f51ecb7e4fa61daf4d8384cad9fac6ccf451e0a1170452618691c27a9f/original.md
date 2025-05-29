```
getexperimentbyname(instance::MLFlow, experiment_name::String)
```

Get metadata for an [`Experiment`](@ref).

This endpoint will return deleted experiments, but prefers the active [`Experiment`](@ref) if an active and deleted [`Experiment`](@ref) share the same name. If multiple deleted experiments share the same name, the API will return one of them.

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `experiment_name`: Name of the associated [`Experiment`](@ref).

# Returns

An instance of type [`Experiment`](@ref).
