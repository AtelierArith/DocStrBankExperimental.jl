```
center3pts(a::Point, b::Point, c::Point)
```

Find the radius and center point for three points lying on a circle.

returns `(centerpoint, radius)` of a circle.

If there's no such circle, the function returns `(Point(0, 0), 0)`.

If two of the points are the same, use `circle(pt1, pt2)` instead.
