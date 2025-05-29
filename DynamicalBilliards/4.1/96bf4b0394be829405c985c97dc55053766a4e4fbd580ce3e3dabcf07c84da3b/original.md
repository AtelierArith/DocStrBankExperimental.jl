```
Billiard(obstacles...)
```

Construct a `Billiard` from given `obstacles` (tuple, vector, varargs).

For functions like [`boundarymap`](@ref), it is expected (if possible) that the obstacles of the billiard are sorted, such that the arc-coordinate `ξ` around the billiard is increasing counter-clockwise.

`ξ` is measured as:

  * the distance from start point to end point in `Wall`s
  * the arc length measured counterclockwise from the open face in `Semicircle`s
  * the arc length measured counterclockwise from the rightmost point in `Circular`s
