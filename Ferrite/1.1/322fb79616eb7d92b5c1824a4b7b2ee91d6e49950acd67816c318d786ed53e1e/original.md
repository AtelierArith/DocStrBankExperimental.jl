```
SparsityPattern(nrows::Int, ncols::Int; nnz_per_row::Int = 8)
```

Create an empty [`SparsityPattern`](@ref) with `nrows` rows and `ncols` columns. `nnz_per_row` is used as a memory hint for the number of non zero entries per row.

`SparsityPattern` is the default sparsity pattern type for the standard DofHandler and is therefore commonly constructed using [`init_sparsity_pattern`](@ref) instead of with this constructor.

# Examples

```julia
# Create a sparsity pattern for an 100 x 100 matrix, hinting at 10 entries per row
sparsity_pattern = SparsityPattern(100, 100; nnz_per_row = 10)
```

# Methods

The following methods apply to `SparsityPattern` (see their respective documentation for more details):

  * [`add_sparsity_entries!`](@ref): convenience method for calling [`add_cell_entries!`](@ref), [`add_interface_entries!`](@ref), and [`add_constraint_entries!`](@ref).
  * [`add_cell_entries!`](@ref): add entries corresponding to DoF couplings within the cells.
  * [`add_interface_entries!`](@ref): add entries corresponding to DoF couplings on the interface between cells.
  * [`add_constraint_entries!`](@ref): add entries resulting from constraints.
  * [`allocate_matrix`](@ref allocate_matrix(::SparsityPattern)): instantiate a matrix from the pattern. The default matrix type is `SparseMatrixCSC{Float64, Int}`.
