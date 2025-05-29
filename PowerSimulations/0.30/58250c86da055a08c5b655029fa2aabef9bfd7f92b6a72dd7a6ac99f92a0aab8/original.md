```julia
read_aux_variable(
    res::PowerSimulations.SimulationProblemResults{PowerSimulations.DecisionModelSimulationResults},
    args...;
    initial_time,
    count,
    store
) -> DataStructures.SortedDict{Any, Any, Base.Order.ForwardOrdering}

```

Return the values for the requested auxillary variables. It keeps requests when performing multiple retrievals.

# Arguments

  * `args`: Can be a string returned from [`list_aux_variable_names`](@ref) or args that can be splatted into a AuxVarKey.
  * `initial_time::Dates.DateTime` : initial of the requested results
  * `count::Int`: Number of results
