```
FD_rich(trait_matrix::Trait_Matrix, weight, display_graph::Bool)
```

Calculate the functional richness of a trait matrix using Gower distance and PCA.

# Arguments

  * `trait_matrix::Trait_Matrix`: A trait matrix containing trait values for different species.
  * `weight`: Vector of weight parameters for each traits in the trait matrix. Can be missing, in this case, each traits are consider equals.
  * `display_graph::Bool`: A boolean flag indicating whether to display the graph.

# Returns

  * `rich`: Functional richness value.

# Details

The function computes the Gower distance matrix from the trait matrix and performs Principal Component Analysis (PCA) on it.  It then projects the data onto the first two principal components and computes the convex hull of the projected points.  If `display_graph` is set to true, it generates a scatter plot of the projected points with the convex hull highlighted. Finally, it calculates the functional richness using Gauss' shoelace formula for the area of the convex hull.
