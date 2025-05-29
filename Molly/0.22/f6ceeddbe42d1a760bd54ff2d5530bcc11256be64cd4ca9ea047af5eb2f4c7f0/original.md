```
simulate_remd!(sys, remd_sim, n_steps; n_threads=Threads.nthreads(),
               run_loggers=true, rng=Random.default_rng())
```

Run a REMD simulation on a [`ReplicaSystem`](@ref) using a REMD simulator.

Not currently compatible with interactions that depend on step number.
