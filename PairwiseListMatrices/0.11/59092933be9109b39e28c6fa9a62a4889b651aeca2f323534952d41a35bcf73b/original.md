Returns the `k` index of the `list` from the indixes `i` and `j` with `i<j` from a matrix of `nelements` by `nelements`. `diagonal` should be `true` or `Val{true}` if the diagonal values are on the `list`. You must not use it with `i>j`.

```jldoctest
julia> using PairwiseListMatrices

julia> plm = PairwiseListMatrix([10,20,30,40,50,60], true)
3×3 PairwiseListMatrix{Int64,true,Array{Int64,1}}:
 10  20  30
 20  40  50
 30  50  60

julia> ij2k(1, 2, 3, true)
2

julia> getlist(plm)[2]
20

```
