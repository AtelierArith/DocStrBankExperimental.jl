```
intersectionlinecircle(p1::Point, p2::Point, cpoint::Point, r)
```

Find the intersection points of a line (extended through points `p1` and `p2`) and a circle.

Return a tuple of `(n, pt1, pt2)`

where

  * `n` is the number of intersections, `0`, `1`, or `2`
  * `pt1` is first intersection point, or `Point(0, 0)` if none
  * `pt2` is the second intersection point, or `Point(0, 0)` if none

The calculated intersection points won't necessarily lie on the line segment between `p1` and `p2`.
