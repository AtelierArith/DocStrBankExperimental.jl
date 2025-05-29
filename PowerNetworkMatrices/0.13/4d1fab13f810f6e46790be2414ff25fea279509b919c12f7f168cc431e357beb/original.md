The Virtual Power Transfer Distribution Factor (VirtualPTDF) structure gathers the rows of the PTDF matrix as they are evaluated on-the-go. These rows are evalauted independently, cached in the structure and do not require the computation of the whole matrix (therefore significantly reducing the computational requirements).

The VirtualPTDF is initialized with no row stored.

The VirtualPTDF is indexed using branch names and bus numbers as for the PTDF matrix.

# Arguments

  * `K::KLU.KLUFactorization{Float64, Int}`:       LU factorization matrices of the ABA matrix, evaluated by means of KLU
  * `BA::SparseArrays.SparseMatrixCSC{Float64, Int}`:       BA matric
  * `ref_bus_positions::Set{Int}`:       Vector containing the indexes of the columns of the BA matrix corresponding       to the reference buses
  * `dist_slack::Vector{Float64}`:       Vector of weights to be used as distributed slack bus.       The distributed slack vector has to be the same length as the number of buses.
  * `axes<:NTuple{2, Dict}`:       Tuple containing two vectors: the first one showing the branches names,       the second showing the buses numbers. There is no link between the       order of the vector of the branches names and the way the PTDF rows are       stored in the cache.
  * `lookup<:NTuple{2, Dict}`:       Tuple containing two dictionaries, mapping the branches       and buses with their enumerated indexes. The branch indexes refer to       the key of the cache dictionary. The bus indexes refer to the position       of the elements in the PTDF row stored.
  * `temp_data::Vector{Float64}`:       Temporary vector for internal use.
  * `valid_ix::Vector{Int}`:       Vector containing the row/columns indices of matrices related the buses       which are not slack ones.
  * `cache::RowCache`:       Cache were PTDF rows are stored.
  * `subnetworks::Dict{Int, Set{Int}}`:       Dictionary containing the subsets of buses defining the different subnetwork of the system.
  * `tol::Base.RefValue{Float64}`:       Tolerance related to scarification and values to drop.
  * `radial_network_reduction::RadialNetworkReduction`:       Structure containing the radial branches and leaf buses that were removed       while evaluating the matrix
