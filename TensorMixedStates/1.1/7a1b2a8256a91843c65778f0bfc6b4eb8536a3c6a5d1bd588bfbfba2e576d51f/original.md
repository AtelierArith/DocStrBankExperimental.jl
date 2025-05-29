```
approx_W(evolver, t, ::State; options...)
approx_W(evolver, t, ::Simulation; options...)
```

time evolution using approximation WI or WII at a given order. Also see `ApproxWObserver`

# Options

  * `coefs`: coefficients for time dependent evolution
  * `n_symmetrize`: make hermitian (for mixed states) every n_symmetrize steps (default 0 for no corrections)
  * `nsweeps`: number of steps (time step is t / nsweeps)
  * `order`: order of approximation
  * `w`: 1 or 2 for WI or WII
  * `observer!`: observer (see ApproxWObserver)
  * `time_start`: the simulation time at the beginning of evolution
  * `limits`: MPS constraints
