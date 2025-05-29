```
setexperimenttag(instance::MLFlow, experiment_id::String, key::String, value::String)
setexperimenttag(instance::MLFlow, experiment_id::Integer, key::String, value::String)
setexperimenttag(instance::MLFlow, experiment::Experiment, key::String, value::String)
```

Set a tag on an [`Experiment`](@ref). [`Experiment`](@ref) tags are metadata that can be updated.

# Arguments

  * `experiment_id`: ID of the [`Experiment`](@ref) under which to log the tag.
  * `key`: Name of the tag.
  * `value`: String value of the tag being logged.

# Returns

`true` if successful. Otherwise, raises exception.
