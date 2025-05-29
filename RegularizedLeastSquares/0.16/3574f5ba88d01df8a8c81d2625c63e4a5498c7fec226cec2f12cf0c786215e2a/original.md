```
init!(solver::AbstractLinearSolver, state::AbstractSolverState, b::AbstractMatrix; scheduler = SequentialState, kwargs...)
```

Initialize the solver with each column of `b` and pass the corresponding states to the scheduler.
