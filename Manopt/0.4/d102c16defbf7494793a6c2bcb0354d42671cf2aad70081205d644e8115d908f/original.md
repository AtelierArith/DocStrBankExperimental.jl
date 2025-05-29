```
step_solver!(amp::AbstractManoptProblem, dss::DebugSolverState, i)
```

Extend the `i`th step of the solver by a hook to run debug prints, that were added to the `:BeforeIteration` and `:Iteration` entries of the debug lists.
