`combinations(mset[,k];dict=false)`,  `ncombinations(mset[,k];dict=false)`

`combinations`   returns  all  combinations  of   the  multiset  `mset`  (a collection  or  iterable  with  possible  repetitions). If a second integer argument  `k` is given, it returns  the combinations with `k` elements. `k` may  also be a vector  of integers, then it  returns the combinations whose number of elements is one of these integers.

`ncombinations` returns (faster) the number of combinations.

A  *combination* is an unordered subsequence.

By  default, the elements of `mset`  are assumed sortable and a combination is  represented by a sorted `Vector`.  The combinations with a fixed number `k`  of  elements  are  listed  in  lexicographic order. If the elements of `mset`  are not sortable but hashable, the keyword `dict=true` can be given and the (slightly slower) computation is done using a `Dict`.

If  `mset` has  no repetitions,  the list  of all  combinations is just the *powerset* of `mset`.

```julia-repl
julia> ncombinations([1,2,2,3])
12

julia> combinations([1,2,2,3])
12-element Vector{Vector{Int64}}:
 []
 [1]
 [2]
 [3]
 [1, 2]
 [1, 3]
 [2, 2]
 [2, 3]
 [1, 2, 2]
 [1, 2, 3]
 [2, 2, 3]
 [1, 2, 2, 3]
```

The combinations are implemented by an iterator [`Combinations`](@ref)  which can enumerate  the combinations of a large multiset.
