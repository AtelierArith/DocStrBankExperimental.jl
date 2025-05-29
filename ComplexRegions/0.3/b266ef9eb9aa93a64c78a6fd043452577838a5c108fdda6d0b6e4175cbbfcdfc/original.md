```
Circle(zc, r, ccw=true)
```

Construct the circle with given center `zc`, radius `r`, and orientation (defaults to counterclockwise).

```
Circle(a, b, c)
```

Construct the circle passing through the given three numbers. Orientation is determined so that the values are visited in the given order. If the three points are collinear (including when one of the given values is infinite), a `Line` is returned instead.
