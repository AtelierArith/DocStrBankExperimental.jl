```
maximum_weight_maximal_matching{T<:Real}(g, w::Dict{Edge,T})
```

Given a bipartite graph `g` and an edge map `w` containing weights associated to edges, returns a matching with the maximum total weight among the ones containing the greatest number of edges.

Edges in `g` not present in `w` will not be considered for the matching.

A `cutoff` keyword argument can be given, to reduce computational times excluding edges with weights lower than the cutoff.

Finally, a specific algorithm can be chosen (`algorithm` keyword argument); each algorithm has specific dependencies. For instance:

  * If `algorithm=HungarianAlgorithm()` (the default), the package Hungarian.jl is used. This algorithm is always polynomial in time, with complexity O(n³).
  * If `algorithm=LPAlgorithm()`, the package JuMP.jl and one of its supported solvers is required. In this case, the algorithm relies on a linear relaxation on of the matching problem, which is guaranteed to have integer solution on bipartite graphs. A solver must be provided with the `optimizer` keyword parameter.

The returned object is of type `MatchingResult`.
