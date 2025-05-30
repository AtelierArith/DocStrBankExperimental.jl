```
FD_dispersion(trait_matrix::Trait_Matrix, weight)
```

Compute the functional dispersion of a trait matrix using Gower distance and PCA.

# Arguments

  * `trait_matrix::Trait_Matrix`: A trait matrix containing trait values for different species.
  * `weight`: Vector of weight parameters for each traits in the trait matrix. Can be missing, in this case, each traits are consider equals.

# Returns

  * `dispersion`: Functional dispersion value.

# Details

The function computes the Gower distance matrix from the trait matrix and performs Principal Component Analysis (PCA) on it.  It then projects the data onto the first two principal components and computes the convex hull of the projected points.  Next, it calculates the centroid of the convex hull and computes the distance of each point on the hull from the centroid.  The functional dispersion is then calculated as the mean distance of all points on the hull from the centroid.
