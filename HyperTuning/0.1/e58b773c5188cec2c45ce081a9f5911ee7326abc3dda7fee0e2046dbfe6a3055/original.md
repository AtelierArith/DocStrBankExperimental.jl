```
Scenario(;
        parameters...,
        sampler    = default_sampler(),
        pruner     = default_pruner(),
        instances  = [1],
        max_trials = :auto,
        max_evals  = :auto,
        max_time   = :auto,
        verbose    = false,
        batch_size = max(nprocs(), Sys.CPU_THREADS),
    )
```

Define an Scenario with parameters, and budget.

  * `sampler` sampler to be used.
  * `pruner` pruner to reduce computational cost.
  * `instances` array (iterator) containing the problem instances.
  * `max_trials` maximum number of trials to be evaluated on [`optimize`](@ref).
  * `max_evals` maximum number of function evaluations.
  * `max_time` maximum execution time on [`optimize`](@ref).
  * `verbose` show message during the optimization.
  * `batch_size` number of trials evaluated for each instance for each iteration.
