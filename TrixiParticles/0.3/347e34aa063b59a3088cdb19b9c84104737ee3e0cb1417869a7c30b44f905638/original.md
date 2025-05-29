```
SteadyStateReachedCallback(; interval::Integer=0, dt=0.0,
                           interval_size::Integer=10, abstol=1.0e-8, reltol=1.0e-6)
```

Terminates the integration when the change of kinetic energy between time steps falls below the threshold specified by `abstol + reltol * ekin`, where `ekin` is the total kinetic energy of the simulation.

# Keywords

  * `interval=0`:     Check steady state condition every `interval` time steps.
  * `dt=0.0`:         Check steady state condition in regular intervals of `dt` in terms                   of integration time by adding additional `tstops`                   (note that this may change the solution).
  * `interval_size`:  The interval in which the change of the kinetic energy is considered.                   `interval_size` is a (integer) multiple of `interval` or `dt`.
  * `abstol`:         Absolute tolerance.
  * `reltol`:         Relative tolerance.
