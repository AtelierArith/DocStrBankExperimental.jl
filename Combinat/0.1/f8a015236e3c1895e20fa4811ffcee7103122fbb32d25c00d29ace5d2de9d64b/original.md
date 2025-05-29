`tableaux(S)`

if  `S`  is  a  partition  tuple,  returns  the  list  of standard tableaux associated  with  the  partition  tuple  `S`,  that  is  a  filling  of the associated  young diagrams  with the  numbers `1:sum(sum,S)`  such that the numbers increase across the rows and down the columns.

If  `S` is a single partition, the standard tableaux for that partition are returned.

```julia-repl
julia> tableaux([[2,1],[1]])
8-element Vector{Vector{Vector{Vector{Int64}}}}:
 [[[1, 2], [3]], [[4]]]
 [[[1, 2], [4]], [[3]]]
 [[[1, 3], [2]], [[4]]]
 [[[1, 3], [4]], [[2]]]
 [[[1, 4], [2]], [[3]]]
 [[[1, 4], [3]], [[2]]]
 [[[2, 3], [4]], [[1]]]
 [[[2, 4], [3]], [[1]]]

julia> tableaux([2,2])
2-element Vector{Vector{Vector{Int64}}}:
 [[1, 2], [3, 4]]
 [[1, 3], [2, 4]]
```
