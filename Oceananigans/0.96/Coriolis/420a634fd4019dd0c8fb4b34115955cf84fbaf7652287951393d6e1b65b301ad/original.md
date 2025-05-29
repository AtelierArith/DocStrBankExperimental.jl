```
FPlane([FT=Float64;] f=nothing, rotation_rate=Ω_Earth, latitude=nothing)
```

Return a parameter object for constant rotation at the angular frequency `f/2`, and therefore with background vorticity `f`, around a vertical axis. If `f` is not specified, it is calculated from `rotation_rate` and `latitude` (in degrees) according to the relation `f = 2 * rotation_rate * sind(latitude)`.

By default, `rotation_rate` is assumed to be Earth's.

Also called `FPlane`, after the "f-plane" approximation for the local effect of a planet's rotation in a planar coordinate system tangent to the planet's surface.
