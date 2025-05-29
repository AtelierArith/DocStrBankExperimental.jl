`Matrix{Any}`を作成し、ラベルは列1と2に、値は列3に格納されます。対角値はデフォルトで含まれます。

```jldoctest
julia> using PairwiseListMatrices

julia> plm = PairwiseListMatrix([10,20,30], false)
3×3 PairwiseListMatrix{Int64,false,Array{Int64,1}}:
  0  10  20
 10   0  30
 20  30   0

julia> to_table(plm)
6×3 Array{Any,2}:
 "1"  "1"   0
 "1"  "2"  10
 "1"  "3"  20
 "2"  "2"   0
 "2"  "3"  30
 "3"  "3"   0

julia> to_table(plm, diagonal=false)
3×3 Array{Any,2}:   
 "1"  "2"  10
 "1"  "3"  20
 "2"  "3"  30

```
