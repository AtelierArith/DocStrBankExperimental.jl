```
function from_df(df::Array{T,2}, name_list::Vector{String})::GeneralNode{T, Int64} where T<:Real
```

This function takes an adjacency matrix and a vector of names and turns it into a tree. No checks are performed.

Returns the root node of the tree.

  * `df` : matrix with edge weights
  * `name_list` : a list of names such that they match the column indices of the matrix
