```
intersect_geometry(line1::Line2D, line2::Line2D; atol=1e-6)
```

Returns the intersection point if it exists or nothing if they are parallel or coincident.

Equation of line is `ax + by = c`.

Intersection is then the solution of:

```
|a1 b1 | | x | = | c1 |
|a2 b2 | | y |   | c2 |
```
