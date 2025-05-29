```
cross_track_distance(∠distance₁₃::Float64, bearing₁₂::Float64,
bearing₁₃::Float64[, radius::Float64=Rₑ_m])
```

Return the `cross_track_distance` [m] from a point `pos₃` [deg] to a great circle path. The distance is calculated using the angular distance between points `pos₁` and `pos₃` [deg], the `bearing` [deg] between points `pos₁` and `pos₃` [deg] , the `bearing` [deg] between points `pos₁` and `pos₂` [deg], and the `radius` of the earth [m].

Source: www.movable-type.co.uk/scripts/latlong.html
