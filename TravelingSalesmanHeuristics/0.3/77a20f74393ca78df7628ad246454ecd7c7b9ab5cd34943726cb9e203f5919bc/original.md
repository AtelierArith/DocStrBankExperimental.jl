```
nearest_neighbor(distmat)
```

Approximately solve a TSP using the nearest neighbor heuristic. `distmat` is a square real matrix where distmat[i,j] represents the distance from city `i` to city `j`. The matrix needn't be symmetric and can contain negative values. Return a tuple `(path, pathcost)`.

# Optional keyword arguments:

  * `firstcity::Union{Int, Nothing}`: specifies the city to begin the path on. Passing `nothing` or   not specifying a value corresponds to random selection.
  * `closepath::Bool = true`: whether to include the arc from the last city visited back to the   first city in cost calculations. If true, the first city appears first and last in the path.
  * `do2opt::Bool = true`: whether to refine the path found by 2-opt switches (corresponds to   removing path crossings in the planar Euclidean case).
