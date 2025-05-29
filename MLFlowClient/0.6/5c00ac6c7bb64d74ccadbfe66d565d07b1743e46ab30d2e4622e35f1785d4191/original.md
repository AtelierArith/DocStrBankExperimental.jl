```
restorerun(instance::MLFlow, run_id::String)
restorerun(instance::MLFlow, run::Run)
```

Restore a deleted [`Run`](@ref).

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `run_id`: ID of the [`Run`](@ref) to restore.

# Returns

`true` if successful. Otherwise, raises exception.
