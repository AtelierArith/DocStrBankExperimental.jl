`nelements`のペアワイズ測定または比較に必要なリストの長さを返します。`diagonal`が`true`の場合、対角値がリストに含まれます。

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
