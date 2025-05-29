```
updateregisteredmodel(instance::MLFlow, name::String;
    description::Union{String, Missing}=missing)
```

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `name`: [`RegisteredModel`](@ref) unique name identifier.
  * `description`: If provided, updates the description for this [`RegisteredModel`](@ref).

# Returns

An instance of type [`RegisteredModel`](@ref).
