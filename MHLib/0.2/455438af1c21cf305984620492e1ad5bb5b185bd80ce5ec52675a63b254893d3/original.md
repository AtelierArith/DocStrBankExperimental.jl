```
Scheduler(solution, methods, consider_initial_sol)
```

Create a `MHMethod` scheduler.

Create a Scheduler for the given solution with the given methods provides as `Vector{MHMethod}`. If `consider_initial_sol` is `true`, consider the given solution as valid initial solution; otherwise it is assumed to be uninitialized.
