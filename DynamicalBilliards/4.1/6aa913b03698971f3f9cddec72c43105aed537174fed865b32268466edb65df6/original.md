```
escapetime([p,] bd, t; warning = false)
```

Calculate the escape time of a particle `p` in the billiard `bd`, which is the time until colliding with any "door" in `bd`. As a "door" is considered any [`FiniteWall`](@ref) with field `isdoor = true`.

If the particle evolves for more than `t` (integer or float) without colliding with the `Door` (i.e. escaping) the returned result is `Inf`.

A warning can be thrown if the result is `Inf`. Enable this using the keyword `warning = true`.

If a particle is not given, a random one is picked through [`randominside`](@ref). See [`parallelize`](@ref) for a parallelized version.
