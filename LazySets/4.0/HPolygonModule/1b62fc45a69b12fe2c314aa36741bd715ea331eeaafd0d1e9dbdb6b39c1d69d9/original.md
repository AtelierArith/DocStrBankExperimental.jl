# Extended help

```
σ(d::AbstractVector, P::HPolygon;
  [linear_search]::Bool=(length(P.constraints) < 10))
```

### Input

  * `linear_search` – (optional, default: see below) flag for controlling whether                    to perform a linear search or a binary search

### Output

The result is always one of the vertices; in particular, if the direction has norm zero, any vertex is returned.

### Algorithm

Comparison of directions is performed using polar angles; see the definition of `⪯` for two-dimensional vectors.

For polygons with 10 or more constraints we use a binary search by default.
