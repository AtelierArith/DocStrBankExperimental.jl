```julia
export_optimizer_stats(
    res::InfrastructureSystems.Results,
    directory::AbstractString;
    format
) -> Any

```

Save the optimizer statistics to CSV or JSON

# Arguments

  * `res::Union{OptimizationProblemResults, SimulationProblmeResults`: Results
  * `directory::AbstractString` : target directory
  * `format = "CSV"` : can be "csv" or "json
