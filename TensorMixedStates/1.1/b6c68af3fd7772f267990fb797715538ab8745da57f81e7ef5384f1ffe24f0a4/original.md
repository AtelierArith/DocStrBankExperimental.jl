A phase type for time evolution

# Examples

```
Evolve(duration = 2., time_step = 0.1, algo = Tdvp(), evolver = -im*(Z(1)Z(2)+(Z(2)Z(3))), measures = [X, Y, Z])
```

# Fields

  * `limits`: a Limits object to set cutoff and maxdim (see `Limits`)
  * `duration`: the duration of the time evolution
  * `time_step`: the time step
  * `algo`: the algorithm used (one of `Tdvp()` or `ApproxW(...)`)
  * `evolver`: the hamiltonian (evolver = -im * H) with a possible dissipator (evolver = -im * H + D)
  * `measures`: the measurement to make (default [])
  * `measures_period`: number of time steps between measurments (default 1)
