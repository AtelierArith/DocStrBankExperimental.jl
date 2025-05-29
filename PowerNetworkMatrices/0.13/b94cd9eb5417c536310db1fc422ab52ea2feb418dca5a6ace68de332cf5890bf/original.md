Structure containing the ABA matrix and other relevant data.

# Arguments

  * `data::SparseArrays.SparseMatrixCSC{Float64, Int}`:       the ABA matrix coming from the product between the Incidence Matrix A and       the Matrix BA.
  * `axes<:NTuple{2, Dict}`:       Tuple containing two identical vectors, both containing the number of       each bus of the network (each one related to a row/column of the Matrix       in "data"), excluding the slack buses.
  * `lookup<:NTuple{2, Dict}`:       Tuple containing 2 Dictionaries mapping the number of rows and columns       with the number of the buses.
  * `ref_bus_positions::Set{Int}`:       Vector containing the indexes of the columns of the BA matrix corresponding       to the reference buses
  * `K<:Union{Nothing, KLU.KLUFactorization{Float64, Int}}`:       either nothing or a container for KLU factorization matrices (LU factorization)
  * `radial_network_reduction::RadialNetworkReduction`:       Structure containing the radial branches and leaf buses that were removed       while evaluating the matrix
