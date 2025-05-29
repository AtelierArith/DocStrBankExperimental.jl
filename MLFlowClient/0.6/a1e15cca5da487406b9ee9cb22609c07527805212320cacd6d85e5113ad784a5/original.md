```
deleterun(instance::MLFlow, run_id::String)
deleterun(instance::MLFlow, run::Run)
```

Mark a [`Run`](@ref) for deletion.

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `run_id`: ID of the [`Run`](@ref) to delete.

# Returns

`true` if successful. Otherwise, raises exception.
