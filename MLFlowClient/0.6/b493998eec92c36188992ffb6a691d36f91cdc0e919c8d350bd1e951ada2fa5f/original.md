```
deleteexperimentpermission(instance::MLFlow, experiment_id::String, username::String)
deleteexperimentpermission(instance::MLFlow, experiment_id::Integer, username::String)
deleteexperimentpermission(instance::MLFlow, experiment::Experiment, username::String)
```

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `experiment_id`: [`Experiment`](@ref) id.
  * `username`: [`User`](@ref) username.

# Returns

`true` if successful. Otherwise, raises exception.
