```
mass_densities(eos, p, T, flashed_mixture)
```

Compute mass densities for a flashed two-phase mixture.

Always returns a named tuple of (ρ*l, ρ*v), even if the mixture is single-phase.

The value in the absent phase will be that of the present phase for single-phase conditions.
