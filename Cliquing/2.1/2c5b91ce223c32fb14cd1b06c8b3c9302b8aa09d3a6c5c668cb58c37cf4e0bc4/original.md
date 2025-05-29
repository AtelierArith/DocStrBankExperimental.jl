```
struct GreedyClique
    vertices::BitArray
    mutuals::BitArray
end
```

# Arguments

  * `vertices::BitArray`: Vertices in the subgraph that defines a clique. BitVector ranging   over the number of vertex in the full graph that are true if identifies as a member of   the clique and false otherwise.
  * `mutuals::BitArray`: Vertices that neighbour the clique (potential clique members)
