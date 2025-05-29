```
UpdateCallback(; interval::Integer, dt=0.0)
```

Callback to update quantities either at the end of every `interval` time steps or in intervals of `dt` in terms of integration time by adding additional `tstops` (note that this may change the solution).

# Keywords

  * `interval=1`: Update quantities at the end of every `interval` time steps.
  * `dt`: Update quantities in regular intervals of `dt` in terms of integration time       by adding additional `tstops` (note that this may change the solution).
