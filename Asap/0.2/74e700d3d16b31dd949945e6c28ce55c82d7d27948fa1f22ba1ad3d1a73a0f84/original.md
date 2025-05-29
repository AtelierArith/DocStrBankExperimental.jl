```
Network(nodes::Vector{FDMnode}, elements::Vector{FDMelement}, loads::Vector{FDMload})
```

A FDM network defined by a collection of nodes, elements, and loads.

# Fields

  * `nodes::Vector{FDMnode}` collection of nodes in network
  * `elements::Vector{FDMelement}` collection of elements in network
  * `loads::Vector{FDMload}` collection of external loads in network
  * `q::Vector{<:Real}` vector of elemental force densities [n_e × 1]
  * `Q::SparseMatrixCSC{Float64, Int64}` diagonalized sparse matrix of `q` [n*e × n*e]
  * `C::SparseMatrixCSC{Int64, Int64}` element/node connectivity matrix [n*e × n*n]
  * `N::Vector{Int64}` vector of free node indices
  * `F::Vector{Int64}` vector of fixed node indices
  * `Cn::SparseMatrixCSC{Int64, Int64}` connectivity matrix of free nodes = `C[:, N]`
  * `Cf::SparseMatrixCSC{Int64, Int64}` connectivity matrix of fixed nofes = `C[:. F]`
  * `P::Matrix{<:Real}` external load matrix [n_n × 3]
  * `Pn::Matrix{<:Real}` loads applied to free nodes = `P[N, :]`
  * `xyz::Matrix{<:Real}` positions of all nodes [n_n × 3]
