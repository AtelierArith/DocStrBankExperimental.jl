PairwiseListMatrixのラベルを取得します。

```jldoctest
julia> using PairwiseListMatrices

julia> plm  = PairwiseListMatrix(ones(3), false)
3×3 PairwiseListMatrix{Float64,false,Array{Float64,1}}:
 0.0  1.0  1.0
 1.0  0.0  1.0
 1.0  1.0  0.0

julia> getlabels(plm)
3-element Array{String,1}:
 "1"
 "2"
 "3"

julia> nplm  = setlabels(plm, ["a","b","c"])
3×3 Named PairwiseListMatrix{Float64,false,Array{Float64,1}}
A ╲ B │   a    b    c
──────┼──────────────
a     │ 0.0  1.0  1.0
b     │ 1.0  0.0  1.0
c     │ 1.0  1.0  0.0

julia> getlabels(nplm)
3-element Array{String,1}:
 "a"
 "b"
 "c"

```
