```
polyintersect(pgon1::AbstractVector{Point}, pgon2::AbstractVector{Point})
```

Return an array (possibly empty) containing the polygon(s) that define the intersection between the two polygons, `pgon1` and `pgon2`.

The `pgon1` and `pgon2` polygons must not have holes, and cannot be self-intersecting.
