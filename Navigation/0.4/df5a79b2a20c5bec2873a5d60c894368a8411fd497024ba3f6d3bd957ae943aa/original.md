```
along_track_distance(∠distance₁₃::Float64, cross_track_∠distance::Float64,
[radius::Float64=Rₑ_m])
```

The `along_track_distance` from the start point `pos₁` [deg] to the closest point on the great circle path (defined by angular distance `∠distance₁₃` [deg] between `pos₁` and `pos₃` [deg] and the cross track angular distance `cross_track_∠distance` [deg]) to the point `pos₃` [deg]. Optionally a different `radius` for the earth can be used.

Source: www.movable-type.co.uk/scripts/latlong.html
