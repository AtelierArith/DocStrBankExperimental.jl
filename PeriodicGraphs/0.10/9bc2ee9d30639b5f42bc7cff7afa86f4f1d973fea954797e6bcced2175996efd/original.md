```
swap_axes!(g::PeriodicGraph, t)
```

In-place modifies graph `g` so that the new initial cell corresponds to the previous one with its axes swapped according to the permutation `t`.

!!! note
    The resulting graph is isomorphic to the initial one, only the representation has changed.

