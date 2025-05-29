# `partial_duplication`

A random graph model based off of the evolution of protein-protein interaction networks. The method takes an undirected graph and runs a number of steps  which randomly selects an existing vertex, duplicates the node, and keeps the edges between its neighbor with a given probability.

## Input

  * 'A::MatrixNetwork{T}': an undirected seed MatrixNetwork.
  * `steps::Int': The number of steps to run the procedure.
  * `p::Float64': the probability to included each edge after duplication.

Reference:      A duplication growth model of gene expression networks      Ashish Bhan, David J Galas, T. Gregory Dewey     https://doi.org/10.1093/bioinformatics/18.11.1486

## Output

  * A new undirected matrix network generated through the partial duplication  procedure.
  * 'duplicated_vertices::Array{Int,1}': The list of vertices duplicated.
