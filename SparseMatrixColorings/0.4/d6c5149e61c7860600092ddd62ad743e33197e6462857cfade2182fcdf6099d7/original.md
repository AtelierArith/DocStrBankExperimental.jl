```
coloring(
    S::AbstractMatrix,
    problem::ColoringProblem,
    algo::GreedyColoringAlgorithm;
    [decompression_eltype=Float64, symmetric_pattern=false]
)
```

Solve a [`ColoringProblem`](@ref) on the matrix `S` with a [`GreedyColoringAlgorithm`](@ref) and return an [`AbstractColoringResult`](@ref).

The result can be used to [`compress`](@ref) and [`decompress`](@ref) a matrix `A` with the same sparsity pattern as `S`. If `eltype(A) == decompression_eltype`, decompression might be faster.

For a `:nonsymmetric` problem (and only then), setting `symmetric_pattern=true` indicates that the pattern of nonzeros is symmetric. This condition is weaker than the symmetry of actual values, so it can happen for some Jacobians. Specifying it allows faster construction of the bipartite graph.

# Example

```jldoctest
julia> using SparseMatrixColorings, SparseArrays

julia> S = sparse([
           0 0 1 1 0 1
           1 0 0 0 1 0
           0 1 0 0 1 0
           0 1 1 0 0 0
       ]);

julia> problem = ColoringProblem(; structure=:nonsymmetric, partition=:column);

julia> algo = GreedyColoringAlgorithm(; decompression=:direct);

julia> result = coloring(S, problem, algo);

julia> column_colors(result)
6-element Vector{Int64}:
 1
 1
 2
 1
 2
 3

julia> collect.(column_groups(result))
3-element Vector{Vector{Int64}}:
 [1, 2, 4]
 [3, 5]
 [6]
```

# See also

  * [`ColoringProblem`](@ref)
  * [`GreedyColoringAlgorithm`](@ref)
  * [`AbstractColoringResult`](@ref)
  * [`compress`](@ref)
  * [`decompress`](@ref)
