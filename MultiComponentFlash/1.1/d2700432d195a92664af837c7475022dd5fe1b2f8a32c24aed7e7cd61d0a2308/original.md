```
lbc_viscosities(eos, p, T, flashed_mixture)
```

Compute phase viscosities for a flashed two-phase mixture using the LBC correlation.

Always returns a named tuple of (μ*l, μ*v), even if the mixture is single-phase.

The value in the absent phase will be that of the present phase for single-phase conditions.
