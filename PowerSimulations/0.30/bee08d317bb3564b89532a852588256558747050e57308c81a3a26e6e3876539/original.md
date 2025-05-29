```julia
read_optimizer_stats(
    store::PowerSimulations.HdfSimulationStore,
    simulation_step::Int64,
    model_name::Symbol,
    execution_index::Int64
) -> Any

```

Read the optimizer stats for a problem execution.
