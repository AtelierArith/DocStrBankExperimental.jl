```
angular_distance(point₃::Point, point₁::Point, azimuth₁₂::Float64)
```

Return the `angular_distance` [deg] from point₃ [deg] to the closest point on a great circle line starting in `point₁` [deg] with `azimuth₁₂` [deg] from `point₁` to `point₂`. It is assumed that the great circle line does not stop in `point₂`, but continuous around the unit sphere. A positive value indicates being right of the line, and negative being left of the line.

Source: www.movable-type.co.uk/scripts/latlong.html
