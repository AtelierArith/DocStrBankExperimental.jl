```
carc(centerpoint::Point, radius, angle1, angle2; action=:none)
carc(centerpoint::Point, radius, angle1, angle2, action)
```

Add an arc centered at `centerpoint` to the current path from `angle1` to `angle2`, going counterclockwise.

Angles are defined relative to the x-axis, positive clockwise.

See also: `arc()`, `carc2r()`, `carc2sagitta()`, ...
