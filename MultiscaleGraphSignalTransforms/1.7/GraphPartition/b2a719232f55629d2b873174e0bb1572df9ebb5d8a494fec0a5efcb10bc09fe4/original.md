```
GProws, GPcols = partition_tree_matrixDhillon(matrix::Matrix{Float64})

Recursively partition the rows and columns of the matrix using the
bipartite model proposed by Dhillon in "Co-clustering documents and words
using Bipartite Spectral Graph Partitioning"
```

### Input Arguments

  * `matrix::Matrix{Float64}`: an input matrix

### Output Argument

  * `GProws::GraphPart`: partitioning using rows as samples
  * `GPcols::GraphPart`: partitioning using cols as samples
