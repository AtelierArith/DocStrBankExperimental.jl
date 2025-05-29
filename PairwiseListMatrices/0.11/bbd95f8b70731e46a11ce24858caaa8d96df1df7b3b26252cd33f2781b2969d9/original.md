Returns the list length needed for a pairwise measures or comparisons of `nelements`. If `diagonal` is `true`, diagonal values are included in the list.

```jldoctest
julia> using PairwiseListMatrices

julia> plm = PairwiseListMatrix([1, 2, 3, 4, 5, 6], false)
4×4 PairwiseListMatrix{Int64,false,Array{Int64,1}}:
 0  1  2  3
 1  0  4  5
 2  4  0  6
 3  5  6  0

julia> lengthlist(4, false)
6

julia> lengthlist(plm)
6

```
