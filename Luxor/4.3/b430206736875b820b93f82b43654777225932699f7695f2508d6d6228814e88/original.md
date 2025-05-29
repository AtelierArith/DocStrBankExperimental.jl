```
polyhull(ptspgon::Vector{Point})
```

Find all points in `pts` that form a convex hull around the points in `pts`, and return them.

This uses the Graham Scan algorithm.
