```
function default_graph_sitenodes(N::Int)
```

Given the total number of sites, `N::Int`, generates the default hierarchical binary tree graph and a `Dict{Int, Int2}` object that maps each site to the corresponding node. Automatically handles situations where the number of sites is not a power of 2.

#### Return values:

  * `::Graph{Int2}`: Default hierarchical tree graph to accomodate `N` number of sites in a TTN.
  * `::Dict{Int, Int2}`: Maps each site to the corresponding node.

#### Example:

```
graph, sitenodes = default_graph_sitenodes(32)

sitenodes[1] == (1,1) # true
sitenodes[2] == (1,1) # true
sitenodes[3] == (1,2) # true
sitenodes[4] == (1,2) # true
sitenodes[31] == (1,16) # true
sitenodes[32] == (1,16) # true
```
