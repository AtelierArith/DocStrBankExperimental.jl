```
restoreexperiment(instance::MLFlow, experiment_id::String)
restoreexperiment(instance::MLFlow, experiment_id::Integer)
restoreexperiment(instance::MLFlow, experiment::Experiment)
```

Restore an [`Experiment`](@ref) marked for deletion. This also restores associated metadata, runs, metrics, params, and tags. If [`Experiment`](@ref) uses FileStore, underlying artifacts associated with [`Experiment`](@ref) are also restored.

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `experiment_id`: ID of the associated [`Experiment`](@ref).

# Returns

`true` if successful. Otherwise, raises exception.
