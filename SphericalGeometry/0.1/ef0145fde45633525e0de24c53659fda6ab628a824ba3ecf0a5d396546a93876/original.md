```
angular_distance(angular_distance₁₃::Float64, azimuth₁₃::Float64,
azimuth₁₂::Float64)
```

Return the `angular_distance` [deg] from point₃ [deg] to the closest point on a great circle line starting in `point₁` [deg] with `azimuth₁₂` [deg]. For the calculation we need the `angular_distance₁₃` and `azimuth₁₃` between `point₁` and `point₃` [deg], and the `azimuth₁₂` from `point₁` to `point₂` along the great circle line. It is assumed that the great circle line does not stop in `point₂`, but continuous around the unit sphere.

Source: www.movable-type.co.uk/scripts/latlong.html
