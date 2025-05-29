```
edgesubgraph_isomorphisms(
    g::SimpleGraph, h::SimpleGraph;
    vmatch=(g,h)->true, ematch=(g,h)->true,
    kwargs...) -> Iterator
```

Return an iterator that generate isomorphic mappings between `H` and edge-induced subgraphs of `G`. The returned iterator has `ig => ih` pairs that correspond to the indices of matching edges in `G` and `H`, respectively.

`vmatch` and `ematch` control the features needed to be counted as a match.

See `Graphs.induced_subgraph` to construct the subgraphs that result from the match.
