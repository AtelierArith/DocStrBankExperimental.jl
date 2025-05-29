Power Transfer Distribution Factors (PTDF) indicate the incremental change in real power that occurs on transmission lines due to real power injections changes at the buses.

The PTDF struct is indexed using the Bus numbers and Branch names.

# Arguments

  * `data<:AbstractArray{Float64, 2}`:       the transposed PTDF matrix.
  * `axes<:NTuple{2, Dict}`:       Tuple containing two vectors: the first one showing the bus numbers,       the second showing the branch names. The information contained in this       field matches the axes of the fiels `data`.
  * `lookup<:NTuple{2, Dict}`:       Tuple containing two dictionaries mapping the bus numbers and branch       names with the indices of the matrix contained in `data`.
  * `subnetworks::Dict{Int, Set{Int}}`:       dictionary containing the set of bus indexes defining the subnetworks       of the system.
  * `tol::Base.RefValue{Float64}`:       tolerance used for sparsifying the matrix (dropping element whose       absolute value is below this threshold).
  * `radial_network_reduction::RadialNetworkReduction`:       Structure containing the radial branches and leaf buses that were removed       while evaluating the matrix
