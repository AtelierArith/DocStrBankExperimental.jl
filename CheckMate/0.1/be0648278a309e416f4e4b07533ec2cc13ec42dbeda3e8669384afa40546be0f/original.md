```
run_checkset(data, checkset::CheckSet; threaded::Bool=false)::CheckSummary
```

Execute a complete set of validation checks on the provided data.

Runs all checks in a given CheckSet, with options for sequential or parallel execution.

# Arguments

  * `data`: The dataset to be validated (must support Tables.jl interface)
  * `checkset::CheckSet`: A collection of checks to be performed
  * `threaded::Bool`: Whether to run checks in parallel (default: false)

# Returns

A `CheckSummary` containing:

  * Name of the checkset
  * Results of individual checks
  * Total execution time

# Examples

```julia
summary = run_checkset(dataset, payment_checks, threaded=true)
```
