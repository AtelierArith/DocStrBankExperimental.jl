```
createregisteredmodel(instance::MLFlow, name::String;
    tags::MLFlowUpsertData{Tag}=Tag[], description::Union{String, Missing}=missing)
```

Create a [`RegisteredModel`](@ref) with a name. Returns the newly created [`RegisteredModel`](@ref). Validates that another [`RegisteredModel`](@ref) with the same name does not already exist and fails if another [`RegisteredModel`](@ref) with the same name already exists.

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `name`: Register models under this name.
  * `tags`: A collection of [`Tag`](@ref).
  * `description`: Optional description for [`RegisteredModel`](@ref).

# Returns

An instance of type [`RegisteredModel`](@ref).
