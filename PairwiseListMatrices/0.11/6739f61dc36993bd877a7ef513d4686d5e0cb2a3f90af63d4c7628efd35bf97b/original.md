The `apply2upper` function applies the `fun` function over the upper triangular  part of the `PairwiseListMatrix`. Set `use_diag` to `true` if the diagonal  needs to be included in the iteration. The function should take four  arguments, first the `list` and diag fields of the `PairwiseListMatrix`,  the second is the index `k` over that `list`, and the third and fourth are  the `i` and `j` indexes for the position `k` in the upper triangular  part of the matrix. 

```jldoctest
julia> using PairwiseListMatrices

julia> plm = PairwiseListMatrix([1,2,3], true)
2×2 PairwiseListMatrix{Int64,true,Array{Int64,1}}:
 1  2
 2  3

julia> mat = zeros(Int, 2, 2)
2×2 Array{Int64,2}:
 0  0
 0  0

julia> apply2upper((list, k, i, j) -> mat[i, j] = list[k], plm; use_diag = true)

julia> mat
2×2 Array{Int64,2}:
 1  2
 0  3

```
