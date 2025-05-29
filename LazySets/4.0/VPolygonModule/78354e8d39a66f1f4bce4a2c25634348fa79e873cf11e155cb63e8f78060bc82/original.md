```
remove_redundant_vertices!(P::VPolygon;
                           [algorithm]::String="monotone_chain")
```

Remove the redundant vertices from the given polygon in-place.

### Input

  * `P`         – polygon in vertex representation
  * `algorithm` – (optional, default: "monotone_chain") the algorithm used to                compute the convex hull

### Output

The modified polygon whose redundant vertices have been removed.

### Algorithm

A convex-hull algorithm is used to compute the convex hull of the vertices of the polygon `P`; see `?convex_hull` for details on the available algorithms. The vertices are sorted in counter-clockwise fashion.
