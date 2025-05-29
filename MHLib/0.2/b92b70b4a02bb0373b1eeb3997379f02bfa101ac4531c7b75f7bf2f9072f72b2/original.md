```
k_flip_neighborhood_search!(::BoolVectorSolution, k::Int, best_improvement::Bool)
```

Perform one major iteration of a `k`-flip local search, i.e., search one neighborhood.

If `best_improvement` is set, the neighborhood is completely searched and a best neighbor is kept; otherwise the search terminates in a first-improvement manner, i.e., keeping a first encountered better solution. The new bijective value is returned.
