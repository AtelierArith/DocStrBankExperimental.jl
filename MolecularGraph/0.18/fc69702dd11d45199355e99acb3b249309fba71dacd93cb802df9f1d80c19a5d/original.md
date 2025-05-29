```
nodesubgraph_isomorphisms(g::SimpleGraph, h::SimpleGraph; kwargs...) -> Iterator
```

Return an iterator that generate isomorphic mappings between `H` and node-induced subgraphs of `G`. The returned iterator has `ig => ih` pairs that correspond to the indices of matching nodes in `G` and `H`, respectively.
