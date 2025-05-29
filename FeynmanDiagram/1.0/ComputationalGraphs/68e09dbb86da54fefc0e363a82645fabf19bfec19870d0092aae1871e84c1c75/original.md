```
function replace_subgraph(g::AbstractGraph, w::AbstractGraph, m::AbstractGraph)

Creates a modified copy of `g` by replacing the subgraph `w` with a new graph `m`.
For Feynman diagrams, subgraphs `w` and `m` should have the same diagram type, orders, and external indices.
```

# Arguments:

  * `g::AbstractGraph`: graph to be modified
  * `w::AbstractGraph`: subgraph to replace
  * `m::AbstractGraph`: new subgraph
