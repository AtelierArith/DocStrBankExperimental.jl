```
PointHook(p::Point, in_direction)
PointHook(x, y, in_direction)
```

`Hook` defined by a point and a direction (an angle CCW from the positive x axis).

Attaching two `PointHook`s will match the points, oriented so the angles are opposite. By convention, hooks point inward.
