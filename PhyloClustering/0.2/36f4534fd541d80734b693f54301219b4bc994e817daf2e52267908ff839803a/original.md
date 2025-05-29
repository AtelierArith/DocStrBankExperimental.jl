```
plot_clusters(tree::AbstractMatrix{<:Real}, label::Vector{Int64})
```

Visualize the result of models.

# Arguments

  * `tree`: a B * N tree Matrix (each column of tree Matrix is a B-dimensional tree in bipartiton format).
  * `label`: an N-length Vector containing predicted labels for each tree. People can use the output of the models.

# Output

A scatter plot showing tree clusters.
