The macro `@iterateupper` iterates over the upper triangular part of the `PairwiseListMatrix` that is given as first argument. The second argument should be `true` if the diagonal need to be included in the iteration or `false` otherwise. The last argument is the body of the loop, where `list` is the list and diag fields of the `PairwiseListMatrix` and `k` is the index over that `list`. You can also use the respective `i` and `j` indexes for that position `k` in the upper triangular part of the matrix. Other variables are expanded in the current scope. You must not modify the values of `i`, `j` or `k`.

```jldoctest
julia> using PairwiseListMatrices

julia> PLM = PairwiseListMatrix([1,2,3], true)
2×2 PairwiseListMatrix{Int64,true,Array{Int64,1}}:
 1  2
 2  3

julia> mat = zeros(Int, 2, 2)
2×2 Array{Int64,2}:
 0  0
 0  0

julia> let mat = mat # To avoid using global
           @iterateupper PLM true mat[i,j] = list[k]
       end

julia> mat
2×2 Array{Int64,2}:
 1  2
 0  3

```
