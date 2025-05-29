```julia
find_subnetworks(M, bus_numbers)

```

Finds the subnetworks present in the considered System. This is evaluated by taking a the ABA or Adjacency Matrix.

# Arguments

  * `M::SparseArrays.SparseMatrixCSC`:       input sparse matrix.
  * `bus_numbers::Vector{Int}`:       vector containing the indices of the system's buses.
