```
getexperimentpermission(instance::MLFlow, experiment_id::String, username::String)
getexperimentpermission(instance::MLFlow, experiment_id::Integer, username::String)
getexperimentpermission(instance::MLFlow, experiment::Experiment, username::String)
```

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `experiment_id`: [`Experiment`](@ref) id.
  * `username`: [`User`](@ref) username.

# Returns

An instance of type [`ExperimentPermission`](@ref).
