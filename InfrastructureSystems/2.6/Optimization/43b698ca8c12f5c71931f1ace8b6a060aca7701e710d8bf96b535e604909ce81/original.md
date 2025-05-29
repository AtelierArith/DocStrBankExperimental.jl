```julia
read_variables(
    res::InfrastructureSystems.Optimization.OptimizationProblemResults,
    variables;
    kwargs...
) -> Dict{String, DataFrames.DataFrame}

```

Return the values for the requested variable keys for a problem. Accepts a vector of keys for the return of the values.

# Arguments

  * `variables::Vector{Tuple{Type{<:VariableType}, Type{<:PSY.Component}}` : Tuple with variable type and device type for the desired results
  * `start_time::Dates.DateTime` : initial time of the requested results
  * `len::Int`: length of results
