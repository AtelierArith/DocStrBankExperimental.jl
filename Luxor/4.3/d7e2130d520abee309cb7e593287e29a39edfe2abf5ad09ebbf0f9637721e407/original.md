```
polycentroid(pts::Vector{Point}))
```

Find the centroid of a simple polygon.

Returns a point. This only works for simple (non-intersecting) polygons.

You could test the point using `isinside()`.
