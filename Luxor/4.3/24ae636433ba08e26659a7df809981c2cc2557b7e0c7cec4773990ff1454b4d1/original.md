```
ispointonline(pt::Point, pt1::Point, pt2::Point;
    extended = false,
    atol = 10E-5)
```

Return `true` if the point `pt` lies on a straight line between `pt1` and `pt2`.

If `extended` is false (the default) the point must lie on the line segment between `pt1` and `pt2`. If `extended` is true, the point lies on the line if extended in either direction.
