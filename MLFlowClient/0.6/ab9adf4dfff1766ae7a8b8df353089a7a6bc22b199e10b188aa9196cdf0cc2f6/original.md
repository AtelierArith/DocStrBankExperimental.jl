```
setregisteredmodelalias(instance::MLFlow, name::String, alias::String, version::String)
```

# Arguments

  * `instance:` [`MLFlow`](@ref) configuration.
  * `name:` Name of the [`RegisteredModel`](@ref).
  * `alias:` Name of the alias.
  * `version:` [`ModelVersion`](@ref) number.

# Returns

`true` if successful. Otherwise, raises exception.
