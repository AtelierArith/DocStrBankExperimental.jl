```
inedgevals(g::AbstractValGraph, v [, key])
```

Return an iterator of edge values of ingoing edges from neighbors of `v`.

If `g` has multiple edge values, the key cannot be omitted. The order of the neighbors is the same as for `inneighbors(g, v)`.
