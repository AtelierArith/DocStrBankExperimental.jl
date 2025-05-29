```
simulate!(system, simulator, n_steps; <keyword arguments>)
simulate!(system, simulator; <keyword arguments>)
```

Run a simulation on a system according to the rules of the given simulator.

Custom simulators should implement this function.

# Arguments

  * `n_threads=Threads.nthreads()`: the number of threads to run the simulation on, only   relevant when running on CPU.
  * `run_loggers`: whether to run the loggers during the simulation. Can be `true`, `false`   or `:skipzero`, in which case the loggers are not run before the first step. `run_loggers`   is `true` by default except for [`SteepestDescentMinimizer`](@ref), where it is `false`.
  * `rng=Random.default_rng()`: the random number generator used for the simulation. Setting   this allows reproducible stochastic simulations.
