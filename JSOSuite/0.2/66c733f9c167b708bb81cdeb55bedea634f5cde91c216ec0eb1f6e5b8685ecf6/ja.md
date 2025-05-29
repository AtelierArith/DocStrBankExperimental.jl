```
solve!(solver::AbstractOptimizationSolver, model::Union{AbstractNLPModel, JuMP.Model}; kwargs...)
solve!(solver::AbstractOptimizationSolver, model::Union{AbstractNLPModel, JuMP.Model}, stats; kwargs...)
```

`JSOSuite` の `SolverCore.solve!` の拡張。最初の引数は `SolverCore.AbstractOptimizationSolver` 型である必要があります。例えば、`JSOSuite.optimizers[!, :name_solver]` を参照してください。
