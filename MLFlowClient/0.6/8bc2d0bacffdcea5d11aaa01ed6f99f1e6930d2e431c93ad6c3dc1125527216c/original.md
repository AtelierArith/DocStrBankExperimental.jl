```
getlatestmodelversions(instance::MLFlow, name::String;
    stages::Array{String}=String[])
```

# Arguments

  * `instance:` [`MLFlow`](@ref) configuration.
  * `stages:` List of stages.

# Returns

Latest [`ModelVersion`](@ref) for each requests stage.
