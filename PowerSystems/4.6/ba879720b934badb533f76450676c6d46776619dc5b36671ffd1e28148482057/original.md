```julia
to_json(
    sys::PowerSystems.System,
    filename::AbstractString;
    user_data,
    pretty,
    force,
    runchecks
)

```

Serializes a system to a JSON file and saves time series to an HDF5 file.

# Arguments

  * `sys::System`: system
  * `filename::AbstractString`: filename to write

# Keyword arguments

  * `user_data::Union{Nothing, Dict} = nothing`: optional metadata to record
  * `pretty::Bool = false`: whether to pretty-print the JSON
  * `force::Bool = false`: whether to overwrite existing files
  * `check::Bool = false`: whether to run system validation checks

Refer to [`check_component`](@ref) for exceptions thrown if `check = true`.
