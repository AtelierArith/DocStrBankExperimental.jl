```
step_solver!(amp::AbstractManoptProblem, rss::RecordSolverState, i)
```

Extend the `i`th step of the solver by a hook to run records, that were added to the `:Iteration` entry.
