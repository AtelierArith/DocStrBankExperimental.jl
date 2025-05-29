```julia
read_variable(
    res::InfrastructureSystems.Optimization.OptimizationProblemResults,
    args...;
    kwargs...
) -> DataFrames.DataFrame

```

Return the values for the requested variable key for a problem. Accepts a vector of keys for the return of the values.

# Arguments

  * `variable::Tuple{Type{<:VariableType}, Type{<:PSY.Component}` : Tuple with variable type and device type for the desired results
  * `start_time::Dates.DateTime` : start time of the requested results
  * `len::Int`: length of results
