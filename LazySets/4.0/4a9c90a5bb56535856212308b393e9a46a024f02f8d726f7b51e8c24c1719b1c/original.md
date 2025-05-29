```
convex_hull(X::LazySet, Y::LazySet; [algorithm]=nothing,
            [backend]=nothing, [solver]=nothing)
```

Compute the convex hull of two polytopic sets.

### Input

  * `X`         – polytopic set
  * `Y`         – polytopic set
  * `algorithm` – (optional, default: `nothing`) the convex-hull algorithm
  * `backend`   – (optional, default: `nothing`) backend for polyhedral                computations (used for higher-dimensional sets)
  * `solver`    – (optional, default: `nothing`) the linear-programming solver                used in the backend

### Output

If the sets are empty, the result is an `EmptySet`. If the convex hull consists of a single point, the result is a `Singleton`. If the input sets are one-dimensional, the result is an `Interval`. If the input sets are two-dimensional, the result is a `VPolygon`. Otherwise the result is a `VPolytope`.

### Algorithm

We compute the vertices of both `X` and `Y` using `vertices_list` and then compute the convex hull of the union of those vertices.
