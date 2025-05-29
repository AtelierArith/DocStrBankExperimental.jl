```
laplacian_matrix(g, [T=eltype(g)]; dir=:out)
```

Laplacian matrix of graph `g`, defined as

$$
D - A
$$

where $D$ is degree matrix and $A$ is adjacency matrix from `g`.

# Arguments

  * `g`: Should be a adjacency matrix, `FeaturedGraph`, `SimpleGraph`, `SimpleDiGraph` (from Graphs)   or `SimpleWeightedGraph`, `SimpleWeightedDiGraph` (from SimpleWeightedGraphs).
  * `T`: The element type of result degree vector. The default type is the element type of `g`.
  * `dir::Symbol`: The way to calculate degree of a graph `g` regards its directions.   Should be `:in`, `:out`, or `:both`.
