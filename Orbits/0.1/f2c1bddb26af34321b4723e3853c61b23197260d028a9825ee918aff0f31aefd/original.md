```
relative_position(::AbstractOrbit, t)
```

The relative position, `[x, y, z]`, of the companion compared to the host at time `t`. In other words, this is the vector pointing from the host to the companion along the line of sight. Nominally, the units of this distance are relative to the host's radius. For example, a distance of 2 is 2 *stellar* radii.
