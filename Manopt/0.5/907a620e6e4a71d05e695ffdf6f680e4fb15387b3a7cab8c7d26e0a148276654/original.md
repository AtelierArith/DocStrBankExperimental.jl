```
stop_solver!(amp::AbstractManoptProblem, dss::DebugSolverState, k)
```

Extend the `stop_solver!`, whether to stop the solver by a hook to run debug, that were added to the `:Stop` entry of the debug lists.
