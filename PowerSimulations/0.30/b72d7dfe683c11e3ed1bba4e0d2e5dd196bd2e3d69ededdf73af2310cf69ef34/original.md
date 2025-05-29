```julia
read_expression(
    res::PowerSimulations.SimulationProblemResults{PowerSimulations.DecisionModelSimulationResults},
    args...;
    initial_time,
    count,
    store
) -> DataStructures.SortedDict{Any, Any, Base.Order.ForwardOrdering}

```

Return the values for the requested auxillary variables. It keeps requests when performing multiple retrievals.

# Arguments

  * `args`: Can be a string returned from [`list_expression_names`](@ref) or args that can be splatted into a ExpressionKey.
  * `initial_time::Dates.DateTime` : initial of the requested results
  * `count::Int`: Number of results
