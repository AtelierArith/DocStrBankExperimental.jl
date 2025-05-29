Creates a `Matrix{Any}`, labels are stored in the columns 1 and 2, and the values in the column 3. Diagonal values are included by default.

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
