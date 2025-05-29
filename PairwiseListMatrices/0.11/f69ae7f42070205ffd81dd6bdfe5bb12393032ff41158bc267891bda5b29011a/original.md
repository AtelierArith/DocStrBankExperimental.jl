The macro `@iteratediag` writes a `for` loop over the `diag` field of a `PairwiseListMatrix{T,false,VT}` but avoiding calls to `getfield` inside the loop. The first argument of the macro is the `PairwiseListMatrix` that is going to be iterated and the second is the body of the loop. In the body `diag` will be the diag field of the `PairwiseListMatrix` and `k` the index over that vector. Other variables are expanded in the current scope. You must not modify the value of `k`.

```jldoctest
julia> using PairwiseListMatrices

julia> PLM = PairwiseListMatrix([1,2,3], false)
3×3 PairwiseListMatrix{Int64,false,Array{Int64,1}}:
 0  1  2
 1  0  3
 2  3  0

julia> @iteratediag PLM diag[k] += 10k

julia> PLM
3×3 PairwiseListMatrix{Int64,false,Array{Int64,1}}:
 10   1   2
  1  20   3
  2   3  30

```
