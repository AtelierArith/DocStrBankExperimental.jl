```
updateexperimentpermission(instance::MLFlow, experiment_id::String, username::String,
    permission::Permission)
updateexperimentpermission(instance::MLFlow, experiment_id::Integer, username::String,
    permission::Permission)
updateexperimentpermission(instance::MLFlow, experiment::Experiment, username::String,
    permission::Permission)
```

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `experiment_id`: [`Experiment`](@ref) id.
  * `username`: [`User`](@ref) username.
  * `permission`: [`Permission`](@ref) to grant.

# Returns

`true` if successful. Otherwise, raises exception.
