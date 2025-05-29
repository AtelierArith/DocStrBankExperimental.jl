```
subgraph_monomorphisms(g::SimpleGraph, h::SimpleGraph; kwargs...) -> Iterator
```

Generate monomorphism mappings between `H` and subgraphs of `G`. The returned iterator has `ig => ih` pairs that correspond to the indices of matching nodes in `G` and `H`, respectively.
