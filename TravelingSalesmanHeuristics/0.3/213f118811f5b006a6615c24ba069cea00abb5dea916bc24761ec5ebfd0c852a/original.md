```
farthest_insertion(distmat; ...)
```

Generate a TSP path using the farthest insertion strategy. `distmat` must be a square real matrix. Return a tuple `(path, cost)`.

### Optional arguments:

  * `firstCity::Int`: specifies the city to begin the path on. Not specifying a value corresponds   to random selection.
  * `do2opt::Bool = true`: whether to improve the path by 2-opt swaps.
