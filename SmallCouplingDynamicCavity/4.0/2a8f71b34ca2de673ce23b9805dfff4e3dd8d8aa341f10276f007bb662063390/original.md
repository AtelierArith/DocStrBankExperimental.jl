```
bethe_lattice(z::Int, tmax::Int)
```

Generate a Bethe lattice (tree) with a specified degree and depth.

# Arguments

  * `z::Int`: The degree of the Bethe lattice.
  * `tmax::Int`: The maximum depth of the Bethe lattice.

# Returns

  * `V::Vector{Int}`: A list of vertices in the Bethe lattice.
  * `E::Vector{Vector{Int}}`: A list of edges in the Bethe lattice.

# Description

This function generates a Bethe lattice (tree) with a specified degree (`z`) and maximum depth (`tmax`). The Bethe lattice is constructed by iteratively adding nodes and edges according to the specified parameters. The root node is always assigned vertex number 1, and the vertices are numbered in a depth-first manner. The edges are stored as a list of pairs of vertices, where each pair represents an edge between two vertices.

The function returns a tuple where the first element (`V`) is a list of vertices, and the second element (`E`) is a list of edges in the Bethe lattice.
