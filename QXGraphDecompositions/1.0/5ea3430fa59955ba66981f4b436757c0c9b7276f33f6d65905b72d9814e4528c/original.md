```
direct_treewidth_score(G::LabeledGraph, π::Array{Symbol, 1})
```

Return an array of integers, one for each vertex in G, indicating the change in treewidth of G, with respect to π, if that vertex is removed.
