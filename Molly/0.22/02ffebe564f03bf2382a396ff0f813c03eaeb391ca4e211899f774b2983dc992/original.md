```
ReplicaExchangeLogger(n_replicas)
ReplicaExchangeLogger(T, n_replicas)
```

A logger that records exchanges in a replica exchange simulation.

The logged quantities include the number of exchange attempts (`n_attempts`), number of successful exchanges (`n_exchanges`), exchanged replica indices (`indices`), exchange steps (`steps`) and the value of Δ i.e. the argument of Metropolis rate for the exchanges (`deltas`).
