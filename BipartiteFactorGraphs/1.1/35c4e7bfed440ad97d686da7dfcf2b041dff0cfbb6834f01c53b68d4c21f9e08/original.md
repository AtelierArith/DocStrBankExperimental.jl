```
factor_neighbors(g::BipartiteFactorGraph, v::Int)
```

Get all factor neighbors of variable node v. Returns only neighbors that are factor nodes. Note that this is equivalent to `neighbors(g, v)` with extra check that the node is a variable. Use `neighbors(g, v)` for a version that does not check the node type.
