```
outedgevals(g::AbstractValGraph, v [, key])
```

Return an iterator of edge values of outgoing edges from `v` to its neighbors.

If `g` has multiple edge values, the key cannot be omitted. The order of the neighbors is the same as for `outneighbors(g, v)`.
