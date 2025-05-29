```
minimum_weight_perfect_matching(g, w::Dict{Edge,Real})
minimum_weight_perfect_matching(g, w::Dict{Edge,Real}, cutoff)
```

Given a graph `g` and an edgemap `w` containing weights associated to edges, returns a matching with the mimimum total weight among the ones containing exactly `nv(g)/2` edges.

Edges in `g` not present in `w` will not be considered for the matching.

This function relies on the BlossomV.jl package, a julia wrapper around Kolmogorov's BlossomV algorithm.

Eventually a `cutoff` argument can be given, to the reduce computational time excluding edges with weights higher than the cutoff.

The returned object is of type `MatchingResult`.

In case of error try to change the optional argument `tmaxscale` (default is `tmaxscale=10`).
