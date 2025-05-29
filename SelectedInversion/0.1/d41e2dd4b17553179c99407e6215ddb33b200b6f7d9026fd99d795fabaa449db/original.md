```
SupernodalMatrix
```

Represents a sparse block lower triangular matrix with a supernodal layout. A supernode is a set of contiguous columns with identical sparsity pattern below the triangular block at the top. For each supernode, the corresponding nonzero entries are stored in a dense chunk. This enables us to use BLAS for operations on these chunks, so we combine the strengths of sparse and dense matrices.

# Fields

  * `N::Int`: Number of rows
  * `M::Int`: Number of columns
  * `n_super::Int`: Number of supernodes
  * `super_to_col::Vector{Int}`: Start/end column of each supernode.                              Length `n_super + 1`.
  * `col_to_super::Vector{Int}`: Maps each column to its supernode index.                              Length `M`.
  * `super_to_vals::Vector{Int}`: Start/end indices of each supernode into `vals`.                               Length `n_super + 1`.
  * `super_to_rows::Vector{Int}`: Start/end indices of each supernode into `rows`.                               Length `n_super + 1`.
  * `vals::Vector{Float64}`: Nonzero values.
  * `rows::Vector{Int}`: Row indices. CAREFUL: These are zero-indexed!
  * `max_super_rows::Int`: Maximum number of rows below the triangular block in a                        supernode chunk.
  * `transposed_chunks::Bool`: Whether to store the transpose of chunks, such that                            the first axis in the chunk corresponds to the                            columns in the supernode.
  * `symmetric_access::Bool`: Whether to enforce symmetry when accessing entries.
  * `invperm::Vector{Int}`: Permutation to apply before accessing entries                         when `depermuted_access == true`.
  * `depermuted_access::Bool`: Whether to apply an inverse permutation before                            accessing entries.
