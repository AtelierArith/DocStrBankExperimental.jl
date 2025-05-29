`partition(P::CPoset)`

returns  the partition of `1:length(P)` induced by the equivalence relation associated  to  `P`;  that  is,  `i`  and  `j`  are in the same part of the partition  if the `k` such that `i<k` and `j<k` are the same as well as the `k` such that `k<i` and `k<j`.

```julia-repl
julia> p=CPoset([i==j || i%4<j%4 for i in 1:8, j in 1:8])
4,8<1,5<2,6<3,7

julia> partition(p)
4-element Vector{Vector{Int64}}:
 [4, 8]
 [2, 6]
 [3, 7]
 [1, 5]
```

`partition(P::Poset)` returns `partition(P.C)`
