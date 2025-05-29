```
ForceTransform(xA_to_B,θ::Real) -> ForceTransform
```

Computes the 3 x 3 2D Plucker transform matrix for force vectors, transforming from system A to system B. The input `xA_to_B` is the 2-d Euclidean vector from the origin of A to the origin of B, expressed in A coordinates, and `θ` is the angle of system B relative to system A. `xA_to_B` can be in the form of a static vector, a vector, or a tuple.
