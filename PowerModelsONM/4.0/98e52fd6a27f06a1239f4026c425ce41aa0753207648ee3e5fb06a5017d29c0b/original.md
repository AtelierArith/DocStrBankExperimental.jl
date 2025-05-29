```
entrypoint(args::Dict{String,<:Any})::Dict{String,Any}
```

The main ONM Algorithm, performs the following steps:

  * [`initialize_output!`](@ref initialize_output!)
  * [`sanitize_args!`](@ref sanitize_args!)
  * [`setup_logging!`](@ref setup_logging!)
  * [`prepare_data!`](@ref prepare_data!)
  * [`build_solver_instances!`](@ref build_solver_instances!)
  * [`optimize_switches!`](@ref optimize_switches!)
  * [`optimize_dispatch!`](@ref optimize_dispatch!)
  * [`run_stability_analysis!`](@ref run_stability_analysis!)
  * [`run_fault_studies!`](@ref run_fault_studies!)
  * [`analyze_results!`](@ref analyze_results!)

If `args["debug"]` a file containing all data, results, etc. will be written to "debug*onm*yyyy-mm-dd–HH-MM-SS.json"

Returns the full data structure contains all inputs and outputs.
