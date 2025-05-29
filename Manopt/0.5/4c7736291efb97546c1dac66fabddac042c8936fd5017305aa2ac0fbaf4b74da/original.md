```
get_solver_result(ams::AbstractManoptSolverState)
get_solver_result(tos::Tuple{AbstractManifoldObjective,AbstractManoptSolverState})
get_solver_result(o::AbstractManifoldObjective, s::AbstractManoptSolverState)
```

Return the final result after all iterations that is stored within the [`AbstractManoptSolverState`](@ref) `ams`, which was modified during the iterations.

For the case the objective is passed as well, but default, the objective is ignored, and the solver result for the state is called.
