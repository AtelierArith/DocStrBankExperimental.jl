```julia
AdjacencyMatrix(sys; check_connectivity, kwargs...)

```

Builds a AdjacencyMatrix from the system. The return is an N x N AdjacencyMatrix Array indexed with the bus numbers.

# Arguments

  * `check_connectivity::Bool`:       Checks connectivity of the network using Depth First Search (DFS) algorithm
