```
solve!(solver::AbstractOptimizationSolver, model::Union{AbstractNLPModel, JuMP.Model}; kwargs...)
solve!(solver::AbstractOptimizationSolver, model::Union{AbstractNLPModel, JuMP.Model}, stats; kwargs...)
```

`JSOSuite` extension of `SolverCore.solve!`. The first argument should be of type `SolverCore.AbstractOptimizationSolver`, see for instance `JSOSuite.optimizers[!, :name_solver]`.
