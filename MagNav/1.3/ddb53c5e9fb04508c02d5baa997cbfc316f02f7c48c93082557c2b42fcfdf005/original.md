```
fogm(sigma, tau, dt, N)
```

First-order Gauss-Markov stochastic process. Represents unmeasureable time-correlated errors.

**Arguments:**

  * `sigma`: FOGM catch-all bias
  * `tau`:   FOGM catch-all time constant [s]
  * `dt`:    measurement time step [s]
  * `N`:     number of samples (instances)

**Returns:**

  * `x`: FOGM data
