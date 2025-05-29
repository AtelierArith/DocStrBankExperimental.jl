```
make_mat(elements::Vector, rates::Vector, nT::Int)
```

Return an nT x nT sparse matrix T.

# Description

This function returns an nT x nT sparse matrix T, with elements set according to the provided elements and rates.

# Arguments

  * `elements::Vector`: Vector of elements to set in the matrix.
  * `rates::Vector`: Vector of rates corresponding to the elements.
  * `nT::Int`: Size of the matrix (nT x nT).

# Returns

  * `SparseMatrixCSC`: The created sparse matrix T.
