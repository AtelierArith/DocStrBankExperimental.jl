```
AbstractRegion{D}
```

Supertype for all `D` dimensional regions used to define bounds on lattices.

# Implementation

The following should be overriden:

  * `Base.in`: Returns `Bool` on whether a point exists in the region
  * `Base.mod`: Maps points outside the region back into the region
  * `distance`: Calculates distance between points with periodic boundary conditions enabled
