The Virtual Line Outage Distribution Factor (VirtualLODF) structure gathers the rows of the LODF matrix as they are evaluated on-the-go. These rows are evalauted independently, cached in the structure and do not require the computation of the whole matrix (therefore significantly reducing the computational requirements).

The VirtualLODF is initialized with no row stored.

The VirtualLODF struct is indexed using branch names.

# Arguments

  * `K::KLU.KLUFactorization{Float64, Int}`:       LU factorization matrices of the ABA matrix, evaluated by means of KLU.
  * `BA::SparseArrays.SparseMatrixCSC{Float64, Int}`:       BA matrix.
  * `A::SparseArrays.SparseMatrixCSC{Int8, Int}`:       Incidence matrix.
  * `inv_PTDF_A_diag::Vector{Float64}`:       Vector contiaining the element-wise reciprocal of the diagonal elements       coming from multuiplying the PTDF matrix with th Incidence matrix
  * `ref_bus_positions::Set{Int}`:       Vector containing the indexes of the rows of the transposed BA matrix       corresponding to the reference buses.
  * `axes<:NTuple{2, Dict}`:       Tuple containing two vectors showing the branch names.
  * `lookup<:NTuple{2, Dict}`:       Tuple containing two dictionaries, mapping the branches names       the enumerated row indexes indexes.
  * `valid_ix::Vector{Int}`:       Vector containing the row/columns indices of matrices related the buses       which are not slack ones.
  * `temp_data::Vector{Float64}`:       Temporary vector for internal use.
  * `cache::RowCache`:       Cache were LODF rows are stored.
  * `subnetworks::Dict{Int, Set{Int}}`:       Dictionary containing the subsets of buses defining the different subnetwork of the system.
  * `tol::Base.RefValue{Float64}`:       Tolerance related to scarification and values to drop.
  * `radial_network_reduction::RadialNetworkReduction`:       Structure containing the radial branches and leaf buses that were removed       while evaluating the matrix
