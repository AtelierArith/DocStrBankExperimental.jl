```
addnodeset!(grid::AbstractGrid, name::String, nodeid::AbstractVecOrSet{Int})
addnodeset!(grid::AbstractGrid, name::String, f::Function)
```

Adds a `nodeset::OrderedSet{Int}` to the `grid`'s `nodesets` with key `name`. Has the same interface as `addcellset`. However, instead of mapping a cell id to the `String` key, a set of node ids is returned.
