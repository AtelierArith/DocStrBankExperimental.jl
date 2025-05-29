```
function induced_subgraph(g::MetaGraphsNext.MetaGraph, vlist::Vector{String})
```

returns the sub*busses::Vector{String} and sub*edges::Vector{Tuple{String, String}} that are  required to make the induced subgraph in `g` from the nodes (or vertices) in `vlist`.
