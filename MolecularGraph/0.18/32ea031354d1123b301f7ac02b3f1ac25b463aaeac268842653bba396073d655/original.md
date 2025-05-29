```
isomorphisms(g::SimpleGraph, h::SimpleGraph; kwargs...) -> Iterator
```

Return an iterator that generate isomorphic mappings between `G` and `H`. The returned iterator has `ig => ih` pairs that correspond to the indices of matching nodes in `G` and `H`, respectively.
