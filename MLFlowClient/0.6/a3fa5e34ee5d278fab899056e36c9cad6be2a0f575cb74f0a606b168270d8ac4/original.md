```
updatemodelversion(instance::MLFlow, name::String, version::String;
    description::Union{String, Missing}=missing)
```

# Arguments

  * `instance:` [`MLFlow`](@ref) configuration.
  * `name:` Name of the [`RegisteredModel`](@ref).
  * `version:` [`ModelVersion`](@ref) number.
  * `description:` Optional description for [`ModelVersion`](@ref).

# Returns

[`ModelVersion`](@ref) generated for this model in registry.
