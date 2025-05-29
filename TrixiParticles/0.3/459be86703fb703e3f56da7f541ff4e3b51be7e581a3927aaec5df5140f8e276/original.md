```
RoundSphere(; start_angle=0.0, end_angle=2π)
```

Construct a sphere (or sphere segment) by nesting perfectly round concentric spheres. The resulting ball will be perfectly round, but will not have a regular inner structure.

# Keywords

  * `start_angle`: The starting angle of the sphere segment in radians. It determines the                beginning point of the segment. The default is set to `0.0` representing                the positive x-axis.
  * `end_angle`: The ending angle of the sphere segment in radians. It defines the termination              point of the segment. The default is set to `2pi`, completing a full sphere.

!!! note "Usage"
    See [`SphereShape`](@ref) on how to use this.


!!! warning
    The sphere segment is intended for 2D geometries and hollow spheres. If used for filled spheres or in a 3D context, results may not be accurate.

