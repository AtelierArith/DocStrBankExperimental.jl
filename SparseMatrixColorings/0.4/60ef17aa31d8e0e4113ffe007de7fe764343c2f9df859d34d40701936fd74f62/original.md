```
decompress!(
    A::AbstractMatrix, B::AbstractMatrix,
    result::AbstractColoringResult{_,:column/:row}, [uplo=:F]
)

decompress!(
    A::AbstractMatrix, Br::AbstractMatrix, Bc::AbstractMatrix
    result::AbstractColoringResult{_,:bidirectional}
)
```

Decompress `B` (or the tuple `(Br,Bc)`) in-place into `A`, given a coloring `result` of the sparsity pattern of `A`. The out-of-place alternative is [`decompress`](@ref).

!!! note
    In-place decompression is faster when `A isa SparseMatrixCSC`.


Compression means summing either the columns or the rows of `A` which share the same color. It is done by calling [`compress`](@ref).

For `:symmetric` coloring results (and for those only), an optional positional argument `uplo in (:U, :L, :F)` can be passed to specify which part of the matrix `A` should be updated: the Upper triangle, the Lower triangle, or the Full matrix. When `A isa SparseMatrixCSC`, using the `uplo` argument requires a target matrix which only stores the relevant triangle(s).

# Example

```jldoctest
julia> using SparseMatrixColorings, SparseArrays

julia> A = sparse([
           0 0 4 6 0 9
           1 0 0 0 7 0
           0 2 0 0 8 0
           0 3 5 0 0 0
       ]);

julia> result = coloring(A, ColoringProblem(), GreedyColoringAlgorithm());

julia> collect.(column_groups(result))
3-element Vector{Vector{Int64}}:
 [1, 2, 4]
 [3, 5]
 [6]

julia> B = compress(A, result)
4×3 Matrix{Int64}:
 6  4  9
 1  7  0
 2  8  0
 3  5  0

julia> A2 = similar(A);

julia> decompress!(A2, B, result)
4×6 SparseMatrixCSC{Int64, Int64} with 9 stored entries:
 ⋅  ⋅  4  6  ⋅  9
 1  ⋅  ⋅  ⋅  7  ⋅
 ⋅  2  ⋅  ⋅  8  ⋅
 ⋅  3  5  ⋅  ⋅  ⋅

julia> A2 == A
true
```

# See also

  * [`ColoringProblem`](@ref)
  * [`AbstractColoringResult`](@ref)
