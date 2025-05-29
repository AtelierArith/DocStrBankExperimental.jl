```julia
read_parameter(
    res::PowerSimulations.SimulationProblemResults{PowerSimulations.DecisionModelSimulationResults},
    args...;
    initial_time,
    count,
    store
) -> DataStructures.SortedDict{Any, Any, Base.Order.ForwardOrdering}

```

Return the values for the requested parameter. It keeps requests when performing multiple retrievals.

# Arguments

  * `args`: Can be a string returned from [`list_parameter_names`](@ref) or args that can be splatted into a ParameterKey.
  * `initial_time::Dates.DateTime` : initial of the requested results
  * `count::Int`: Number of results
