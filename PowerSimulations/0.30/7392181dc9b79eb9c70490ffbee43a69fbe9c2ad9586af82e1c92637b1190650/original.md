```julia
read_optimizer_stats(
    res::PowerSimulations.SimulationProblemResults;
    store
) -> Any

```

Return the optimizer stats for the problem as a DataFrame.

# Accepted keywords

  * `store::SimulationStore`: a store that has been opened for reading
