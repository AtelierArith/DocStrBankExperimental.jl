```
psos(bd::Billiard, plane::InfiniteWall, t, particles)
```

Compute the Poincaré section of the `particles` with the given `plane`, by evolving each one for time `t` (either integer or float) inside `bd`.

The `plane` can be an [`InfiniteWall`](@ref) of *any* orientation, however only crossings of the `plane` such that `dot(velocity, normal) < 0` are allowed, with `normal` the normal unit vector of the `plane`.

`particles` can be:

  * A single particle.
  * A `Vector` of particles.
  * An integer `n` optionally followed by an angular velocity `ω`.

Return the positions `poss` and velocities `vels` at the instances of crossing the `plane`. If given more than one particle, the result is a vector of vectors of vectors.

*Notice* - This function can handle pinned particles. If a pinned particle can intersect with the `plane`, then an intersection is returned. If however it can't then empty vectors are returned.
