Constructs a matrix of loadings to map `nfactor` latent variables to `nx` observed variables.  The upper triangle is all zeros to enfactororce linear independence among the loading vectors.

# Arguments

  * `values::AbstractVector`: vector of values to put in the nonzero lower triangle. They are

filled in order running down the columns from left to right.

  * `nx::Integer`: Dimension of the data, i.e. the number of rows in the loading matrix
  * `nfactor::Integer`: Number of factors, i.e. the number of columns in the loading matrix
