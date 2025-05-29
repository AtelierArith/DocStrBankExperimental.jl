```
angular_distance(point₃::Point, point₁::Point, point₂::Point)
```

Return the `angular_distance` [deg] from point₃ [deg] to the closest point on a great circle line section starting in `point₁` [deg] and ending in `point₂` [deg]. The great circle line section does not continue around the unit sphere.

The `angular_distance` does not change sign when being left or right of the arc.
