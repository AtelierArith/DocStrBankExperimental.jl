```
struct DistributedLoad
```

A type representing a concentrated load in the finite element model.

  * `ID`: Identification tag of the element to which the distributed load is applied
  * `w_x`: Distributed load acting along the local $x$-direction of the element
  * `w_y`: Distributed load acting along the local $y$-direction of the element
  * `w_z`: Distributed load acting along the local $z$-direction of the element
  * `p`: Fixed-end force vector in the global coordinate system
