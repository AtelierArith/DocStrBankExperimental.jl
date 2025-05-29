```julia
mutable struct BipartiteGraph{I<:Integer, M} <: Graphs.AbstractGraph{I<:Integer}
```

A bipartite graph representation between two, possibly distinct, sets of vertices (source and dependencies). Maps source vertices, labelled `1:N₁`, to vertices on which they depend (labelled `1:N₂`).

# Fields

  * `ne`
  * `fadjlist`
  * `badjlist`
  * `metadata`

# Example

```julia
using ModelingToolkit

ne = 4
srcverts = 1:4
depverts = 1:2

# six source vertices
fadjlist = [[1],[1],[2],[2],[1],[1,2]]

# two vertices they depend on
badjlist = [[1,2,5,6],[3,4,6]]

bg = BipartiteGraph(7, fadjlist, badjlist)
```
