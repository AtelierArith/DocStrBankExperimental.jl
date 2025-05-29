Structure to perform an export from a Sienna System, plus optional updates from `PowerFlowData`, to the PSS/E format. Construct from a `System` and a PSS/E version, update using `update_exporter` with any new data as relevant, and perform the export with `write_export`. Writes a `<name>.raw` file and a `<name>_export_metadata.json` file with transformations that had to be made to conform to PSS/E naming rules, which can be parsed by PowerSystems.jl to perform a round trip with the names restored.

# Arguments:

  * `base_system::PSY.System`: the system to be exported. Later updates may change power flow-related values but may not fundamentally alter the system
  * `psse_version::Symbol`: the version of PSS/E to target, must be one of `PSSE_EXPORT_SUPPORTED_VERSIONS`
  * `write_comments::Bool` = false: whether to add the customary-but-not-in-spec-annotations after a slash on the first line and at group boundaries
  * `name::AbstractString = "export"`: the base name of the export
  * `step::Any = nothing`: optional step data to append to the base export name. User is responsible for updating the step data. If the step data is `nothing`, it is not used; if it is a tuple or vector, it is joined with '*' and concatted; else it is concatted after '*'.
  * `overwrite::Bool = false`: `true` to silently overwrite existing exports, `false` to throw an error if existing results are encountered
