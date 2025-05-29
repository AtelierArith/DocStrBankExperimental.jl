```
resistance_distance_matrix(g)
```

Calculate the resistance distance matrix for a graph.

# Arguments

  * `g`: The graph for which the resistance distance matrix is to be calculated.

# Returns

  * A matrix where the element at the i-th row and j-th column represents the resistance distance between nodes `i` and `j`.

# Notes

  * The resistance distance matrix is calculated using the formula for resistance distance in terms of the Laplacian matrix of the graph.
  * The Laplacian matrix of the graph is calculated using the `laplacian_matrix` function.
  * The pseudoinverse of the Laplacian matrix is calculated using the `pinv` function from the LinearAlgebra module.
