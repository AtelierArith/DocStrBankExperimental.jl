```
getlongwidth(points; n_segments::Int=200)
```

## Description:

Compute the longest internal axis (diameter) of a 2‑D polygon and the widest internal axis perpendicular to it. `points` is the vertices list of the polygon, which is generated by the function `getpolygon` (with order). The function returns the length of the longest axis, its endpoints, the length of the widest axis, and its endpoints.

## Example:

```julia
points = [0.0 0.0; 1.0 0.0; 1.0 1.0; 0.0 1.0]
a, b, c, d, e f = getlongwidth(points)
```
