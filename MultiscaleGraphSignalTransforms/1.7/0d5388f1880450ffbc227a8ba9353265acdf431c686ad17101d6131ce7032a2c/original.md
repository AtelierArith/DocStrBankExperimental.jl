```
SunFlowerGraph(; N = 400)
```

SUNFLOWERGRAPH construct a simple weighted sunflower graph with N vertices. Edge weights are the reciprocal of Euclidean distances.

# Input Arguments

  * `N::Int64`: default is 400, the number of vertices. Requires N > 26.

# Output Argument

  * `G::SimpleWeightedGraph{Int64,Float64}`: a simple weighted graph of the sunflower.
  * `L::Matrix{Float64}`: the weighted unnormalized graph Laplacian matrix.
  * `X::Matrix{Float64}`: a matrix whose i-th row represent the 2D coordinates of the i-th node.
