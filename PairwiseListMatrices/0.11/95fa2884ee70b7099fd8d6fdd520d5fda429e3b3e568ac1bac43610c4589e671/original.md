The macro `@iteratelist` writes a `for` loop over the `list` but avoiding `getfield` calls inside the loop. The first argument of the macro is the `PairwiseListMatrix` that is going to be iterated and the second is the body of the loop. In the body `list` will be the list field of the `PairwiseListMatrix` and `k` the index over that list. Other variables are expanded in the current scope. You must not modify the value of `k`.

```jldoctest
julia> using PairwiseListMatrices

julia> PLM = PairwiseListMatrix([1,2,3], false)
3×3 PairwiseListMatrix{Int64,false,Array{Int64,1}}:
 0  1  2
 1  0  3
 2  3  0

julia> @iteratelist PLM println(list[k])
1
2
3

```
