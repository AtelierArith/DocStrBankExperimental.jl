```julia
AdjacencyMatrix(
    branches,
    buses;
    check_connectivity,
    kwargs...
)

```

Builds a AdjacencyMatrix from a collection of buses and branches. The return is an N x N AdjacencyMatrix Array indexed with the bus numbers.

# Arguments

  * `check_connectivity::Bool`:       Checks connectivity of the network using Depth First Search (DFS) algorithm
