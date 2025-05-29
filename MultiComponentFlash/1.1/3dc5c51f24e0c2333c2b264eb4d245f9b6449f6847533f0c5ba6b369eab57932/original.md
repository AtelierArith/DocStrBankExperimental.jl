```
phase_saturations(eos, p, T, flashed_mixture)
```

Compute phase saturations for a flashed two-phase mixture.

Always returns a named tuple of (S*l, S*v), even if the mixture is single-phase.

The value in the absent phase will be zero.
