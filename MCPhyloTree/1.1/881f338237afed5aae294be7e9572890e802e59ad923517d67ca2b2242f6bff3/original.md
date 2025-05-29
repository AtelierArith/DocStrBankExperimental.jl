```
to_covariance(tree::N, blv::Array{T})::Array{T,2} where {N<:AbstractNode,T<: Real}
```

Calcualte the variance-covariance matrix from `tree`. An entry (i,j) of the matrix is defined as the length of the path connecting the latest common ancestor of i and j with the root of the tree.

Returns an Array of Real numbers.

  * `tree` : Node in tree of interest.
  * `blv` : branchlength vector of tree.
