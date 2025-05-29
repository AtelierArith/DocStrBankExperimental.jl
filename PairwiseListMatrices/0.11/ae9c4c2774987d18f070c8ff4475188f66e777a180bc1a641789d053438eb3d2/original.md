This function takes the filename as first argument and a `PairwiseListMatrix` as second argument. If the `diagonal` keyword argument is `true` (default), the diagonal is included in the output. The keyword argument `delim` (by default is `'	'`) allows to modified the character used as delimiter.

```jldoctest
julia> using PairwiseListMatrices, DelimitedFiles

julia> plm  = PairwiseListMatrix(trues(3), false)
3×3 PairwiseListMatrix{Bool,false,BitArray{1}}:
 false   true   true
  true  false   true
  true   true  false

julia> writedlm("example.csv", plm, diagonal=false, delim=',')

julia> println(read("example.csv", String))
1,2,true
1,3,true
2,3,true

```
