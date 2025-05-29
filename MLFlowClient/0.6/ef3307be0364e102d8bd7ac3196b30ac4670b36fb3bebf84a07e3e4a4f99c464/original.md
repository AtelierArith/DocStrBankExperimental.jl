```
getexperiment(instance::MLFlow, experiment_id::String)
getexperiment(instance::MLFlow, experiment_id::Integer)
```

Get metadata for an [`Experiment`](@ref). This method works on deleted experiments.

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `experiment_id`: ID of the associated [`Experiment`](@ref).

# Returns

An instance of type [`Experiment`](@ref).
