```julia
read_parameters(
    res::InfrastructureSystems.Optimization.OptimizationProblemResults,
    parameters;
    kwargs...
) -> Dict{String, DataFrames.DataFrame}

```

Return the values for the requested parameter keys for a problem. Accepts a vector of keys for the return of the values.

# Arguments

  * `parameters::Vector{Tuple{Type{<:ParameterType}, Type{<:PSY.Component}}` : Tuple with parameter type and device type for the desired results
  * `start_time::Dates.DateTime` : initial time of the requested results
  * `len::Int`: length of results
