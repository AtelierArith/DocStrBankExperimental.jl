```
delaunay(points, options=Quickhull.Options())
```

Compute the d-dimensional Delaunay triangulation of `points`. `points` can be a vector of point-like objects (e.g. `Tuple` or `StaticVector`) or a (D, N)-sized matrix of numbers.

The triangulation is found by lifting into (d+1) dimensions and taking the convex hull.
