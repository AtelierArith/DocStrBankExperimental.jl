```
PressureLogger(n_steps)
PressureLogger(T, n_steps)
```

Log the [`pressure`](@ref) of a system throughout a simulation.

This should only be used on systems containing just pairwise interactions, or where the specific interactions, general interactions and constraints do not contribute to the pressure.
