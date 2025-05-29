## `biconnected_components!`

This function returns the number of biconnected components in the  underlying graph. It expects an undirected graph as its input.

## Functions

  * `number = biconnected_components!(A::MatrixNetwork, articulation::Vector{Bool}, map::Vector{Int64})`

## Inputs

  * `A`: the adjacency matrix.
  * `articulation`: A boolean array, where each element is initialized to false.
  * `map`: Vector of size equal to the number of edges.

## Returns

  * `cn`: The number of biconnected components in the graph

## Example

A = load*matrix*network("biconnected*example") B = MatrixNetwork(A) number*of*components = biconnected*components!(B, zeros(Bool,0), zeros(Int64,0))
