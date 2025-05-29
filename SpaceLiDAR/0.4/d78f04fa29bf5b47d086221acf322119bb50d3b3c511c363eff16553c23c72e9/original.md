```
shift(longitude, latitude, angle, distance)
```

Shift `longitude` and `latitude` with `distance` in [m] in direction `angle`, where North is 0°. Returns a tuple of the shifted coordinates: `(longitude, latitude)`. Useful for offsetting SpaceLiDAR points to the left or right of the track, in combination with [`angle`](@ref).
