```
ppr_diffusion(g::GNNGraph{<:COO_T}, alpha =0.85f0) -> GNNGraph
```

Calculates the Personalized PageRank (PPR) diffusion based on the edge weight matrix of a GNNGraph and updates the graph with new edge weights derived from the PPR matrix. References paper: [The pagerank citation ranking: Bringing order to the web](http://ilpubs.stanford.edu:8090/422)

The function performs the following steps:

1. Constructs a modified adjacency matrix `A` using the graph's edge weights, where `A` is adjusted by `(α - 1) * A + I`, with `α` being the damping factor (`alpha_f32`) and `I` the identity matrix.
2. Normalizes `A` to ensure each column sums to 1, representing transition probabilities.
3. Applies the PPR formula `α * (I + (α - 1) * A)^-1` to compute the diffusion matrix.
4. Updates the original edge weights of the graph based on the PPR diffusion matrix, assigning new weights for each edge from the PPR matrix.

# Arguments

  * `g::GNNGraph`: The input graph for which PPR diffusion is to be calculated. It should have edge weights available.
  * `alpha_f32::Float32`: The damping factor used in PPR calculation, controlling the teleport probability in the random walk. Defaults to `0.85f0`.

# Returns

  * A new `GNNGraph` instance with the same structure as `g` but with updated edge weights according to the PPR diffusion calculation.
