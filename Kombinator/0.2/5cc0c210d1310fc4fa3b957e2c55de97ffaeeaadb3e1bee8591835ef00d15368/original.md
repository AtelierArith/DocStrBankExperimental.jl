```
make_solution(::CombinatorialInstance, ::Dict{K, Float64}) where {K}
```

Creates a solution object of the right type for the given combinatorial  instance. The dictionary gives the solution that should be included in the  returned object. 

As only binary decision variables are supported, the caller of this function  may provide a dictionary such that *either* only the variables that are  included in the solution (i.e. `variable => 1.0` entries) *or* all the  variables, with associated values of 0 (not in the solution) or 1 (in the solution). For instance, if the solution contains only the edge  `1`-`2` out of the two possible edges (the other one being `1`-`3`), there are two equivalent dictionaries that can be passed: either  `Dict(Edge(1, 2) => 1.0)` or `Dict(Edge(1, 2) => 1.0, Edge(1, 3) => 0.0)`.
