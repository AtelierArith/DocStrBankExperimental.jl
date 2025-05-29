```
cheapest_insertion(distmat; ...)
```

Complete a tour using cheapest insertion with a single-city loop as the initial path. Return a tuple `(path, cost)`.

### Optional keyword arguments:

  * `firstcity::Union{Int, Nothing}`: specifies the city to begin the path on. Passing `nothing` or   not specifying a value corresponds to random selection.
  * `do2opt::Bool = true`: whether to improve the path found by 2-opt swaps.
