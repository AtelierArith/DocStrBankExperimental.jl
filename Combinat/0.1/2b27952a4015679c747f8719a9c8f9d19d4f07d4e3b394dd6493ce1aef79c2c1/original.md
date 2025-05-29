`multisets(set,k)`, `nmultisets(set,k)`

`multisets`  returns  the  set  of  all  multisets of length `k` made of elements   of   the   set   `set`   (a   collection  without  repetitions). `nmultisets` returns the number of multisets.

An  *multiset* of length `k` is  an unordered selection with repetitions of length  `k` from `set` and is represented  by a sorted vector of length `k` made  of elements  from `set`  (it is  also sometimes called a "combination with replacement").

```julia-repl
julia> multisets(1:4,3)
20-element Vector{Vector{Int64}}:
 [1, 1, 1]
 [1, 1, 2]
 [1, 1, 3]
 [1, 1, 4]
 [1, 2, 2]
 [1, 2, 3]
 [1, 2, 4]
 [1, 3, 3]
 [1, 3, 4]
 [1, 4, 4]
 [2, 2, 2]
 [2, 2, 3]
 [2, 2, 4]
 [2, 3, 3]
 [2, 3, 4]
 [2, 4, 4]
 [3, 3, 3]
 [3, 3, 4]
 [3, 4, 4]
 [4, 4, 4]
```
