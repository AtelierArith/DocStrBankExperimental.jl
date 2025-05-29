```
loginputs(instance::MLFlow, run_id::String; datasets::Array{DatasetInput})
loginputs(instance::MLFlow, run::Run; datasets::Array{DatasetInput})
```

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `run_id`: ID of the [`Run`](@ref) to log under this field is required.
  * `datasets`: A collection of [`DatasetInput`](@ref) to log.

# Returns

`true` if successful. Otherwise, raises exception.
