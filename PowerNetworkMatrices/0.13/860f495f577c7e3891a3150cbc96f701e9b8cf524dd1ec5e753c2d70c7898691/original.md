Incidence matrix: shows connection between buses, defining lines

# Arguments

  * `data::SparseArrays.SparseMatrixCSC{Int8, Int}`:       the actual Incidence matrix.
  * `axes<:NTuple{2, Dict}`:       Tuple containing two vectors (the first one showing the branches names,       the second showing the buses numbers).
  * `lookup<:NTuple{2, Dict}`:       Tuple containing two dictionaries, the first mapping the branches       and buses with their enumerated indexes.
  * `ref_bus_positions::Set{Int}`:       Vector containing the indices of the reference slack buses.
  * `radial_network_reduction::RadialNetworkReduction`:       Structure containing the radial branches and leaf buses that were removed       while evaluating the matrix
