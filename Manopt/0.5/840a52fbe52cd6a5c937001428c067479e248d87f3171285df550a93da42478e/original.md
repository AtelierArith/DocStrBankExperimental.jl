```
initialize_solver!(ams::AbstractManoptProblem, rss::RecordSolverState)
```

Extend the initialization of the solver by a hook to run records that were added to the `:Start` entry.
