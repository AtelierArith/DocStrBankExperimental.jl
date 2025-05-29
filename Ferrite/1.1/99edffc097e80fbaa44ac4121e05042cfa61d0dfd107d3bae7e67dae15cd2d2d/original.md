```
BlockSparsityPattern(block_sizes::Vector{Int})
```

Create an empty `BlockSparsityPattern` with row and column block sizes given by `block_sizes`.

# Examples

```julia
# Create a block sparsity pattern with block size 10 x 5
sparsity_pattern = BlockSparsityPattern([10, 5])
```

# Methods

The following methods apply to `BlockSparsityPattern` (see their respective documentation for more details):

  * [`add_sparsity_entries!`](@ref): convenience method for calling [`add_cell_entries!`](@ref), [`add_interface_entries!`](@ref), and [`add_constraint_entries!`](@ref).
  * [`add_cell_entries!`](@ref): add entries corresponding to DoF couplings within the cells.
  * [`add_interface_entries!`](@ref): add entries corresponding to DoF couplings on the interface between cells.
  * [`add_constraint_entries!`](@ref): add entries resulting from constraints.
  * [`allocate_matrix`](@ref allocate_matrix(::SparsityPattern)): instantiate a (block) matrix from the pattern. The default matrix type is `BlockMatrix{Float64, Matrix{SparseMatrixCSC{Float64, Int}}}`, i.e. a `BlockMatrix`, where the individual blocks are of type `SparseMatrixCSC{Float64, Int}`.

!!! note "Package extension"
    This functionality is only enabled when the package [BlockArrays.jl](https://github.com/JuliaArrays/BlockArrays.jl) is installed (`pkg> add BlockArrays`) and loaded (`using BlockArrays`) in the session.

