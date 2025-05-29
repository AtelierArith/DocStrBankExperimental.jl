```
solve_tsp(distmat; quality_factor = 40)
```

Approximately solve a TSP by specifying a distance matrix. Return a tuple `(path, cost)`.

The optional keyword `quality_factor` (real number in [0,100]; defaults to 40) specifies the tradeoff between computation time and quality of solution returned. Higher values tend to lead to better solutions found at the cost of more computation time.

!!! note
    It is not guaranteed that a call with a high `quality_factor` will always run slower or return a better solution than a call with a lower `quality_factor`, though this is typically the case. A `quality_factor` of 100 neither guarantees an optimal solution nor the best solution  that can be found via extensive use of the methods in this package.


!!! danger
    TravelingSalesmanHeuristics does not support distance matrices with arbitrary indexing; indices must be `1:n` in both dimensions for `n` cities.


See also: individual heuristic methods such as [`farthest_insertion`](@ref)
