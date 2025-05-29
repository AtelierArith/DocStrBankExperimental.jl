```julia
read_optimizer_stats(
    store::PowerSimulations.HdfSimulationStore,
    simulation_step::Int64,
    model_name::Symbol,
    execution_index::Int64
) -> Any

```

問題実行のための最適化統計を読み取ります。
