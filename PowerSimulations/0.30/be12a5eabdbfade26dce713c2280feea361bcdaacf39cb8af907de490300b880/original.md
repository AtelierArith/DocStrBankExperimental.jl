```julia
read_variable(
    res::PowerSimulations.SimulationProblemResults{PowerSimulations.DecisionModelSimulationResults},
    args...;
    initial_time,
    count,
    store
) -> DataStructures.SortedDict{Any, Any, Base.Order.ForwardOrdering}

```

Return the values for the requested variable. It keeps requests when performing multiple retrievals.

# Arguments

  * `args`: Can be a string returned from [`list_variable_names`](@ref) or args that can be splatted into a VariableKey.
  * `initial_time::Dates.DateTime` : initial of the requested results
  * `count::Int`: Number of results
  * `store::SimulationStore`: a store that has been opened for reading

# Examples

```julia
read_variable(results, ActivePowerVariable, ThermalStandard)
read_variable(results, "ActivePowerVariable__ThermalStandard")
```
