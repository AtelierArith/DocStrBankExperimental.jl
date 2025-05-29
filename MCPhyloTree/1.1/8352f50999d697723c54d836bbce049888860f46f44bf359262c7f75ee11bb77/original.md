```
function cov2tree(covmat::Array{<:T, 2}, names::Vector{<:AbstractString}, numbers::Vector{Int64}; tol::Real=1e-7)::GeneralNode{T, Int64} where T<:Real
```

This function reconstructs a tree from a covariance matrix. It takes a covariance matrix,  a vector of leaf names and a vector of node numbers as mandatory arguments. The order of the two vectors must correspond to the order of rows and columns in the covariance matrix. Optionally, the `tol` paramter indicates  the boundary below which all values are treated as zero.

Returns the root node of the tree corresponding to the supplied covariance matrix.

  * `covmat` : covariance matrix
  * `names` : a list of names such that they match the column/row indices of the matrix
  * `numbers` : a list of Integers such that they match the column/row indices of the matrix
  * `tol` : cut off value below which all values are treated as zero
