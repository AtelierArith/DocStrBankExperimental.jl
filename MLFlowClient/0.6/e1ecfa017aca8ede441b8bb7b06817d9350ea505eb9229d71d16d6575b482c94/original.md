```
createexperiment(instance::MLFlow, name::String;
    artifact_location::Union{String, Missing}=missing,
    tags::MLFlowUpsertData{Tag}=Tag[])
```

Create an [`Experiment`](@ref) with a name. Returns the newly created [`Experiment`](@ref). Validates that another [`Experiment`](@ref) with the same name does not already exist and fails if another [`Experiment`](@ref) with the same name already exists.

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `name`: [`Experiment`](@ref) name. This field is required.
  * `artifact_location`: Location where all artifacts for the [`Experiment`](@ref)   are stored. If not provided, the remote server will select an appropriate   default.
  * `tags`: A collection of [`Tag`](@ref) to set on the [`Experiment`](@ref).

# Returns

The ID of the newly created [`Experiment`](@ref).
