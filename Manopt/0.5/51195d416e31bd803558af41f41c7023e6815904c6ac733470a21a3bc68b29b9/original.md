```
stop_solver!(amp::AbstractManoptProblem, rss::RecordSolverStatek k)
```

Extend the call to the stopping criterion by a hook to run records, that were added to the `:Stop` entry.
