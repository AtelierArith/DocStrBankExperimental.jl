```
remd_exchange!(sys, sim, n, m; n_threads=Threads.nthreads(), rng=Random.default_rng())
```

Attempt an exchange of replicas `n` and `m` in a [`ReplicaSystem`](@ref) during a REMD simulation.

Successful exchanges should exchange coordinates and velocities as appropriate. Returns acceptance quantity `Δ` and a `Bool` indicating whether the exchange was successful.
