```
deleteexperiment(instance::MLFlow, experiment_id::String)
deleteexperiment(instance::MLFlow, experiment_id::Integer)
deleteexperiment(instance::MLFlow, experiment::Experiment)
```

Mark an [`Experiment`](@ref) and associated metadata, runs, metrics, params, and tags for deletion. If the [`Experiment`](@ref) uses FileStore, artifacts associated with [`Experiment`](@ref) are also deleted.

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `experiment_id`: ID of the associated [`Experiment`](@ref).

# Returns

`true` if successful. Otherwise, raises exception.
