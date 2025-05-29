Structure containing the BA matrix and other relevant data.

# Arguments

  * `data::SparseArrays.SparseMatrixCSC{Float64, Int}`:       the transposed BA matrix coming from the product between the Incidence       Matrix A and the Matrix of Susceptance B
  * `axes<:NTuple{2, Dict}`:       Tuple containing two vectors, the first one contains the names of each       buse of the network (each one related to a row of the Matrix in "data"),       the second one contains the names of each line of the network (each one       related to a column of the Matrix in "data")
  * `lookup<:NTuple{2, Dict}`:       Tuple containing 2 Dictionaries mapping the number of rows and columns       with the names of buses and branches
  * `ref_bus_positions::Set{Int}`:       Set containing the indexes of the columns of the BA matrix corresponding       to the reference buses
  * `radial_network_reduction::RadialNetworkReduction`:       Structure containing the radial branches and leaf buses that were removed       while evaluating the matrix
