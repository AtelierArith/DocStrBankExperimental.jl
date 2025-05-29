```julia
SpatialInertia(frame; moment, moment_about_com, com, mass)

```

Construct a `SpatialInertia` by specifying:

  * `frame`: the frame in which the spatial inertia is expressed.
  * one of:

      * `moment`: the moment of inertia expressed in `frame` (i.e., about the origin of `frame` and in `frame`'s axes).
      * `moment_about_com`: the moment of inertia about the center of mass, in `frame`'s axes.
  * `com`: the center of mass expressed in `frame`.
  * `mass`: the total mass.

The `com` and `mass` keyword arguments are required, as well as exactly one of `moment` and `moment_about_com`
