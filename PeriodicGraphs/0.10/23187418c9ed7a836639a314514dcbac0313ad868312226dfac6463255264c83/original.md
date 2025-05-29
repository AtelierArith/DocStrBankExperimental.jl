```
offset_representatives!(g::PeriodicGraph, offsets)
```

In-place modifies graph `g` so that the `i`-th vertex of the new initial cell corresponds to the `i`-th vertex in cell `offsets[i]` compared to the previous initial cell.

!!! note
    The resulting graph is isomorphic to the initial one, only the representation has changed.

