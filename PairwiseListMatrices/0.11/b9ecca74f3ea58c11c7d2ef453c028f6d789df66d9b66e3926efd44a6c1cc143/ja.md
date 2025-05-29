`PairwiseListMatrix{T, false, VT}`から対角値を持つ型`VT`のベクトルを返します。

```jldoctest
julia> using PairwiseListMatrices

julia> plm = PairwiseListMatrix([10,20,30,40,50,60], true)
3×3 PairwiseListMatrix{Int64,true,Array{Int64,1}}:
 10  20  30
 20  40  50
 30  50  60

julia> diagonal(plm)
3-element Array{Int64,1}:
 10
 40
 60

```
