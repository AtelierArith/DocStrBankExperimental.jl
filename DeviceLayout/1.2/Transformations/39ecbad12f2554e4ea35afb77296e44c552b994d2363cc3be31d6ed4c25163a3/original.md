```
Reflection(α; through_pt=nothing)
Reflection(vec::Point; through_pt=nothing)
Reflection(p1::Point, p2::Point)
```

Construct a reflection across a line.

The line can be specified by two points `p1, p2` or by a direction and point `through_pt` the line passes through. The direction can be a vector or an angle made with the positive x axis (units accepted; no units => radians), and the `through_pt` is the origin by default.
