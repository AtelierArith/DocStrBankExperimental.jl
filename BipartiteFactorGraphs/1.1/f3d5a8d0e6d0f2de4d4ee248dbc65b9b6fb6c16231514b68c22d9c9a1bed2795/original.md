```
variable_neighbors(g::BipartiteFactorGraph, v::Int)
```

Get all variable neighbors of factor node v. Returns only neighbors that are variable nodes. Note that this is equivalent to `neighbors(g, v)` with extra check that the node is a factor. Use `neighbors(g, v)` for a version that does not check the node type.
