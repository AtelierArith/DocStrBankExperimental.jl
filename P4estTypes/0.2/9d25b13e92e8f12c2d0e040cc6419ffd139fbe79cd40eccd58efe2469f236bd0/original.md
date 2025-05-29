```
GhostLayer{X,P}
```

Stores a ghost layer of quadrants that neighbor the domain local to the rank for a `Pxest{X}`.  Also stores the corresponding local domain quadrants, mirrors, that are in other rank's ghost layers.

# Fields

  * `pointer`: The pointer (of type `P`) can be a pointer to either a `P4estTypes.P4est.p4est_ghost_t` or a `P4estTypes.P4est.p8est_ghost_t`.  See the help documentation for these types for more information about the underlying p4est structures.

# See also

  * [`ghostlayer`](@ref): a function used to construct a `GhostLayer`
