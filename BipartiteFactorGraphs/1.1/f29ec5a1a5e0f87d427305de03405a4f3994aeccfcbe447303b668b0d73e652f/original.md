```
add_edge!(g::BipartiteFactorGraph{TVar,TFac,E}, var::Int, fac::Int, data::E) where {TVar,TFac,E}
```

Add an edge between variable node `var` and factor node `fac` with associated data. User must ensure that `var` is a variable node and `fac` is a factor node. Edge data is stored with the original order of vertices (var, fac), but can be accessed in either order using get*edge*data.
