```
DMRGObserver(;energy_tol=0.0,
              minsweeps=2,
              energy_type=Float64)
```

Construct a DMRGObserver by providing the energy tolerance used for early stopping, and minimum number of sweeps that must be done.

Optional keyword arguments:

  * energy_tol: if the energy from one sweep to the next no longer changes by more than this amount, stop after the current sweep
  * minsweeps: do at least this many sweeps
  * energy_type: type to use when storing energies at each step
