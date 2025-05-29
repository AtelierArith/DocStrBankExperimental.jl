```
get_EECC(G::SimpleGraph, m₀::Int64)
```

Calculate the edge-disjoint edge clique cover (EECC) of a graph `G` considering cliques of order up to `m₀`, according to the heuristic proposed in the paper.

# Arguments

  * `G::SimpleGraph`: a simple graph of the LightGraphs.SimpleGraph type
  * `m₀::Int64`: an integer representing the maximum order of the cliques to consider

# Return

A vector containing the EECC
