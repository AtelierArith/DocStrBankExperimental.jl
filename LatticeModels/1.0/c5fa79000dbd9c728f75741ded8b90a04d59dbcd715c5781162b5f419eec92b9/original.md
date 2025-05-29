```
Polygon{N}([radius, center])
Polygon{N}([center; h])
```

Construct a regular `N`-sided polygon with a given (circumscribed) radius and center. Note the aliases: `Triangle`, `Square`, and `Hexagon` are `Polygon{3}`, `Polygon{4}`, and `Polygon{6}` respectively.

## Arguments

  * `radius`: The (circumscribed) radius of the polygon.
  * `center`: The center of the polygon.

## Keyword Arguments

  * `h`: The distance from the center to the vertices. If given, the `radius` is calculated as `h / cos(pi / N)`.
