```julia
SpatialInertia(frame, moment, cross_part, mass)

```

Construct a `SpatialInertia` by specifying:

  * `frame`: the frame in which the spatial inertia is expressed.
  * `moment`: the moment of inertia expressed in `frame` (i.e., in `frame`'s axes and about the origin of `frame`).
  * `cross_part`: the center of mass expressed in `frame`, multiplied by the mass.
  * `mass`: the total mass.

For more convenient construction of `SpatialInertia`s, consider using the keyword argument constructor instead.
