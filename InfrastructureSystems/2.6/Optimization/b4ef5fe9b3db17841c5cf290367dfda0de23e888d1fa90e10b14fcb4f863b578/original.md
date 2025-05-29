```julia
read_aux_variables(
    res::InfrastructureSystems.Optimization.OptimizationProblemResults,
    aux_variables;
    kwargs...
) -> Dict{String, DataFrames.DataFrame}

```

Return the values for the requested aux_variable keys for a problem. Accepts a vector of keys for the return of the values.

# Arguments

  * `aux_variables::Vector{Tuple{Type{<:AuxVariableType}, Type{<:PSY.Component}}` : Tuple with aux_variable type and device type for the desired results
  * `start_time::Dates.DateTime` : initial time of the requested results
  * `len::Int`: length of results
