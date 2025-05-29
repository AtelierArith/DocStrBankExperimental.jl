The Line Outage Distribution Factor (LODF) matrix gathers a sensitivity coefficients of how a change in a line's flow affects the flows on other lines in the system.

# Arguments

  * `data<:AbstractArray{Float64, 2}`:       the transposed LODF matrix.
  * `axes<:NTuple{2, Dict}`:       Tuple containing two identical vectors containing the names of the       branches related to each row/column.
  * `lookup<:NTuple{2, Dict}`:       Tuple containing two identical dictionaries mapping the branches        their enumerated indexes (row and column numbers).
  * `tol::Base.RefValue{Float64}`:       tolerance used for sparsifying the matrix (dropping element whose       absolute value is below this threshold).
  * `radial_network_reduction::RadialNetworkReduction`:       Structure containing the radial branches and leaf buses that were removed       while evaluating the matrix
