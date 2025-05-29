```
updaterun(instance::MLFlow, run_id::String; status::Union{RunStatus, Missing}=missing,
    end_time::Union{Int64, Missing}=missing, run_name::Union{String, Missing}=missing)
updaterun(instance::MLFlow, run::Run; status::Union{RunStatus, Missing}=missing,
    end_time::Union{Int64, Missing}=missing, run_name::Union{String, Missing}=missing)
```

Update [`Run`](@ref) metadata.

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `run_id`: ID of the [`Run`](@ref) to update.
  * `status`: Updated status of the [`Run`](@ref).
  * `end_time`: Unix timestamp in milliseconds of when the [`Run`](@ref) ended.
  * `run_name`: Updated name of the [`Run`](@ref).

# Returns

  * An instance of type [`RunInfo`](@ref) with the updated metadata.
