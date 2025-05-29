```
rounded_corner(p0::Point{T}, p1::Point{T}, p2::Point{T}, radius::S;
    atol, min_side_len, min_angle)
```

A vector of points in a circular arc rounding the corner defined by `p0, p1, p2` with `radius`.

## Keyword arguments

  * `atol`: tolerance is approximately the maximum distance from any segment to the actual circle. Defaults to 1.0nm (or 0.001 when not using units).
  * `min_side_len`: the minimum side length that will get rounded (e.g. for 90-degree angles, it makes sense to have `min_side_len = 2 * rounding_radius`).
  * `min_angle`: if adjacent sides are collinear within the tolerance set by `min_angle`, rounding will not be performed.
