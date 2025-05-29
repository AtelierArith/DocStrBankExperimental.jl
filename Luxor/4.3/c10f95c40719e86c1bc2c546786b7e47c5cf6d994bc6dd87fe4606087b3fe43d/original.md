```
arc(centerpoint::Point, radius, angle1, angle2; action=:none)
arc(centerpoint::Point, radius, angle1, angle2, action)
```

Add an arc to the current path from `angle1` to `angle2` going clockwise, centered at `centerpoint`.

Angles are defined relative to the x-axis, positive clockwise.

See also: `carc()`, `arc2r()`, `arc2sagitta()`, ...
