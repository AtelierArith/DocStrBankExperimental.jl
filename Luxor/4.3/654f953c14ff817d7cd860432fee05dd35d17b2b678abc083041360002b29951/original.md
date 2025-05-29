```
polyclip(s, c)
```

Return a polygon that defines the intersection between an subject polygon and the clip polygon.

Return `nothing` if the function can't find one.

  * S - subject polygon - can be concave or convex.
  * C - clip polygon - must be convex.

Uses the Sutherland-Hodgman clipping algorithm. Calls `ispointonleftofline()`.

To find where two polygon intersections, use `polyintersect()`.
