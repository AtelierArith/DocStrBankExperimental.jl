```
struct BlockDiagonalForm
```

A type for storing a block-diagonal form of a matrix.

# Fields

  * `B::DT`: The block-diagonal matrix. It can be a sparse matrix or a [`QuantumObject`](@ref).
  * `P::DT`: The permutation matrix. It can be a sparse matrix or a [`QuantumObject`](@ref).
  * `blocks::AbstractVector`: The blocks of the block-diagonal matrix.
  * `block_sizes::AbstractVector`: The sizes of the blocks.
