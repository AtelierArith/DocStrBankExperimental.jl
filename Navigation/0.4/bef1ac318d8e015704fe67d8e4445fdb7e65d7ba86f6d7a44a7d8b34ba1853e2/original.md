```
intermediate_point(pos₁::Point, pos₂::Point[, fraction::Float64 = 0.5])
```

Return the `intermediate_point` [deg] at any `fraction` along the great circle path between two points with positions `pos₁` and `pos₂` [deg]. The fraction along the great circle route is such that `fraction` = 0.0 is at `pos₁` [deg] and `fraction` 1.0 is at `pos₂` [deg].

Source: www.movable-type.co.uk/scripts/latlong.html
