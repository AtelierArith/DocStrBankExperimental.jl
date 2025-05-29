```
meancollisiontime([p,] bd, t) → κ
```

Compute the mean collision time `κ` of the particle `p` in the billiard `bd` by evolving for total amount `t` (either float for time or integer for collision number).

Collision times are counted only between obstacles that are *not* [`PeriodicWall`](@ref).

If a particle is not given, a random one is picked through [`randominside`](@ref). See [`parallelize`](@ref) for a parallelized version.
