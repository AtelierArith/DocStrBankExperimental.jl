to_df(root::GeneralNode)::Tuple{Array{Float64}, Vector{String}}

This function returns a matrix representation of the tree structure and a vector with the column names. The entry `mat[i,j]` is the length of the edge connecting node `i` with node `j`. Returns Tuple containing the matrix and a vector of names.

  * `root` : root of tree used to create matrix represenation.
