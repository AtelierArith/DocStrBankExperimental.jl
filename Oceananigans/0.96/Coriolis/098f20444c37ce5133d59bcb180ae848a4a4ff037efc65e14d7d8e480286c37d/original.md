```
ConstantCartesianCoriolis([FT=Float64;] fx=nothing, fy=nothing, fz=nothing,
                                        f=nothing, rotation_axis=ZDirection(),
                                        rotation_rate=Ω_Earth, latitude=nothing)
```

Return a parameter object for a constant rotation decomposed into the `x`, `y`, and `z` directions. In oceanography the components `x`, `y`, `z` correspond to the directions east, north, and up. This constant rotation can be specified in three different ways:

  * Specifying all components `fx`, `fy` and `fz` directly.
  * Specifying the Coriolis parameter `f` and (optionally) a `rotation_axis` (which defaults to the `z` direction if not specified).
  * Specifying `latitude` (in degrees) and (optionally) a `rotation_rate` in radians per second (which defaults to Earth's rotation rate).
