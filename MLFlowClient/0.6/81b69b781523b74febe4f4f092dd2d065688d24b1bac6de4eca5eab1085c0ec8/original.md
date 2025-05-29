```
transitionmodelversionstage(instance::MLFlow, name::String, version::String,
    stage::String, archive_existing_versions::Bool)
```

# Arguments

  * `instance:` [`MLFlow`](@ref) configuration.
  * `name:` Name of the [`RegisteredModel`](@ref).
  * `version:` [`ModelVersion`](@ref) number.
  * `stage:` Transition [`ModelVersion`](@ref) to new stage.
  * `archive_existing_versions:` When transitioning a model version to a particular stage,   this flag dictates whether all existing model versions in that stage should be atomically   moved to the “archived” stage. This ensures that at-most-one model version exists in the   target stage.

# Returns

Updated [`ModelVersion`](@ref).
