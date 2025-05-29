The `apply2list` function applies the function `fun`, the first argument, for  each element on `list` but avoiding `getfield` calls inside the loop.  The second argument of the macro is the `PairwiseListMatrix` that will be  iterated. `fun` should take two arguments; the first is the `list` field of  the `PairwiseListMatrix`, and the second is the index over that list at a  given iteration.

```jldoctest
julia> using PairwiseListMatrices

julia> plm = PairwiseListMatrix([1,2,3], false)
3×3 PairwiseListMatrix{Int64,false,Array{Int64,1}}:
 0  1  2
 1  0  3
 2  3  0

julia> apply2list((list, k) -> println(list[k]), plm)
1
2
3

```
