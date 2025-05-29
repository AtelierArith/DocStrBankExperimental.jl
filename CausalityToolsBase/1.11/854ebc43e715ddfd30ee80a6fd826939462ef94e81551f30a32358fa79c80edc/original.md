```
encode(point, reference_point, edgelengths)
```

Encode a point into its integer bin labels relative to some `reference_point` (always counting from lowest to highest magnitudes), given a set of box  `edgelengths` (one for each axis). The first bin on the positive side of  the reference point is indexed with 0, and the first bin on the negative  side of the reference point is indexed with -1.
