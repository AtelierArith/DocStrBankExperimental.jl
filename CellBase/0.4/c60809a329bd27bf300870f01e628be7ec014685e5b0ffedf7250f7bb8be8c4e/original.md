```
ExtendedPointArray(cell::Cell, rcut)
```

Constructed an ExtendedPointArray from a given structure. Implicitly, the positions are wrapped inside the unit cell, even if the actual  in the original Cell is outside the unit cell. This ensures the correct neighbour list begin constructed.
