```
ground_intensity_bound(pp, t, h)
```

Compute a local upper bound on the ground intensity for a temporal point process `pp` applied to history `h` at time `t`.

Return a tuple of the form `(B, L)` satisfying `λg(t|h) ≤ B` for all `u ∈ [t, t+L)`.
