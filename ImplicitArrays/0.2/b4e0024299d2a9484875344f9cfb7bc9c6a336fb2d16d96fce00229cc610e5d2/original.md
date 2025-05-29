```
BlockMatrix{T} <: AbstractArray{T, 2}
```

Implicit block matrix of equally-sized matrices with elements of type `T`.

# Constructors

```
BlockMatrix(blocks)
BlockMatrix{T}(blocks)
BlockMatrix{T}(rows, cols[, blocks...])
BlockMatrix(rows, cols, first_block[, more_blocks...])
```

Create a new block matrix from the given matrix of matrices. Alternatively, create the block matrix from a sequence of matrices, given the number of `rows` and `cols`.

# Examples

```jldoctest; setup = :(using ImplicitArrays)
julia> A = [1 2; 3 4]; B = zeros(Int, 2, 2);

julia> C = [x * y for x in 2:3, y in 3:4];

julia> BlockMatrix(1, 4, A, B, B, C)
2×8 BlockMatrix{Int64}:
 1  2  0  0  0  0  6   8
 3  4  0  0  0  0  9  12
```

!!! note
    This type is not suitable for high-performance purposes, as matrix blocks are stored in an abstract container to allow the composition of arbitrary matrix types. For more details, please refer to the [performance tips](https://docs.julialang.org/en/v1/manual/performance-tips/) in the official Julia documentation.

