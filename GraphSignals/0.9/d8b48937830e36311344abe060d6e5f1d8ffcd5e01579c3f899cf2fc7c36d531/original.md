```
normalized_laplacian(g, [T=float(eltype(g))]; dir=:both, selfloop=false)
```

Normalized Laplacian matrix of graph `g`, defined as

$$
I - D^{-\frac{1}{2}} \tilde{A} D^{-\frac{1}{2}}
$$

where $D$ is degree matrix and $\tilde{A}$ is adjacency matrix w/o self loop from `g`.

# Arguments

  * `g`: Should be a adjacency matrix, `FeaturedGraph`, `SimpleGraph`, `SimpleDiGraph` (from Graphs)   or `SimpleWeightedGraph`, `SimpleWeightedDiGraph` (from SimpleWeightedGraphs).
  * `T`: The element type of result degree vector. The default type is the element type of `g`.
  * `dir::Symbol`: The way to calculate degree of a graph `g` regards its directions.   Should be `:in`, `:out`, or `:both`.
  * `selfloop::Bool`: Adding self loop to $\tilde{A}$ or not.
