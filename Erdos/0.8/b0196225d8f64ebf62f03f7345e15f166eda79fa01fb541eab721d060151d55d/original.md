```
minimum_cut(g, s, t, capacity_matrix=DefaultCapacity(); kws...)
```

Finds the `s-t cut` of minimal weight according to the `capacities` matrix on the directed graph `g`. The solution is found through a maximal flow algorithm. See [`maximum_flow`](@ref) for the optional arguments.

Returns a triple `(f, cut, labels)`, where `f` is the weight of the cut, `cut` is a vector of the edges in the cut, and `labels` gives a partitioning of the vertices in two sets, according to the cut.
