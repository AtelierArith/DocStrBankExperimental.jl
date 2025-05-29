```
QuadrantWrapper{X,P}
```

Stores a Pxest{X} quadrant (where `X=4` indicates a quadrant and `X=8` indicates an octant; quadrant is used both as the general term and the term for the 2D object).

# Fields

  * `pointer`: The pointer (of type `P`) can be a pointer to either a `P4estTypes.P4est.p4est_quadrant` or a `P4estTypes.P4est.p8est_quadrant`.  See the help documentation for these types for more information about the underlying p4est structures.
