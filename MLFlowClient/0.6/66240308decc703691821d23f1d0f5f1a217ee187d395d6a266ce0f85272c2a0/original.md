```
updateexperiment(instance::MLFlow, experiment_id::String, new_name::String)
updateexperiment(instance::MLFlow, experiment_id::Integer, new_name::String)
updateexperiment(instance::MLFlow, experiment::Experiment, new_name::String)
```

Update [`Experiment`](@ref) metadata.

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `experiment_id`: ID of the associated [`Experiment`](@ref).
  * `new_name`: If provided, the [`Experiment`](@ref) name is changed to the new name. The new name   must be unique.

# Returns

`true` if successful. Otherwise, raises exception.
