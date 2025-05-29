```julia
export_realized_results(
    res::InfrastructureSystems.Results
) -> String

```

Save the realized results to CSV files for all variables, paramaters, duals, auxiliary variables, expressions, and optimizer statistics.

# Arguments

  * `res::Results`: Results
  * `save_path::AbstractString` : path to save results (defaults to simulation path)
