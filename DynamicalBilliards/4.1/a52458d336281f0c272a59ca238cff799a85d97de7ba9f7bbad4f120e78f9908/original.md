```
billiard_polygon(n::Int, R, center = [0,0]; setting = "standard")
```

Return a vector of obstacles that defines a regular-polygonal billiard with `n` sides, radius `r` and given `center`.

Note: `R` denotes the so-called outer radius, not the inner one.

### Settings

  * "standard" : Specular reflection occurs during collision.
  * "periodic" : The walls are `PeriodicWall` type, enforcing periodicity at the boundaries. Only available for `n=4` or `n=6`.
  * "random" : The velocity is randomized upon collision.
