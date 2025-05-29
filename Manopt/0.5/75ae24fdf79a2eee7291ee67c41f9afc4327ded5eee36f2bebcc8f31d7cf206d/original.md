```
solve!(p::AbstractManoptProblem, s::AbstractManoptSolverState)
```

run the solver implemented for the [`AbstractManoptProblem`](@ref)`p` and the [`AbstractManoptSolverState`](@ref)`s` employing [`initialize_solver!`](@ref), [`step_solver!`](@ref), as well as the [`stop_solver!`](@ref) of the solver.
