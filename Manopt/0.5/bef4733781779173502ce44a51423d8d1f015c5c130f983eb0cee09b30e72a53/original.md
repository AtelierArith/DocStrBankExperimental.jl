```
initialize_solver!(amp::AbstractManoptProblem, dss::DebugSolverState)
```

Extend the initialization of the solver by a hook to run the [`DebugAction`](@ref) that was added to the `:Start` entry of the debug lists. All others are triggered (with iteration number `0`) to trigger possible resets
