```
σ(d::AbstractVector, P::HPolygonOpt;
  [linear_search]::Bool=(length(P.constraints) < 10))
```

Return a support vector of an optimized polygon in a given direction.

### Input

  * `d`             – direction
  * `P`             – optimized polygon in constraint representation
  * `linear_search` – (optional, default: see below) flag for controlling whether                    to perform a linear search or a binary search

### Output

The support vector in the given direction. The result is always one of the vertices; in particular, if the direction has norm zero, any vertex is returned.

### Algorithm

Comparison of directions is performed using polar angles; see the definition of `⪯` for two-dimensional vectors.

For polygons with 10 or more constraints we use a binary search by default.
