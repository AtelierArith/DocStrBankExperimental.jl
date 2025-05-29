```
decompress_single_color!(
    A::AbstractMatrix, b::AbstractVector, c::Integer,
    result::AbstractColoringResult, [uplo=:F]
)
```

Decompress the vector `b` corresponding to color `c` in-place into `A`, given a `:direct` coloring `result` of the sparsity pattern of `A` (it will not work with a `:substitution` coloring).

  * If `result` comes from a `:nonsymmetric` structure with `:column` partition, this will update the columns of `A` that share color `c` (whose sum makes up `b`).
  * If `result` comes from a `:nonsymmetric` structure with `:row` partition, this will update the rows of `A` that share color `c` (whose sum makes up `b`).
  * If `result` comes from a `:symmetric` structure with `:column` partition, this will update the coefficients of `A` whose value is deduced from color `c`.

!!! warning
    This function will only update some coefficients of `A`, without resetting the rest to zero.


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

julia> A2 = similar(A); A2 .= 0;

julia> decompress_single_color!(A2, B[:, 2], 2, result)
4×6 SparseMatrixCSC{Int64, Int64} with 9 stored entries:
 ⋅  ⋅  4  0  ⋅  0
 0  ⋅  ⋅  ⋅  7  ⋅
 ⋅  0  ⋅  ⋅  8  ⋅
 ⋅  0  5  ⋅  ⋅  ⋅

julia> A2[:, [3, 5]] == A[:, [3, 5]]
true
```

# See also

  * [`ColoringProblem`](@ref)
  * [`AbstractColoringResult`](@ref)
  * [`decompress!`](@ref)
