`permutations(n)`

returns  in lexicographic order the permutations of `1:n`. This is a faster version  of  `arrangements(1:n,n)`.  `permutations`  is  implemented  by an iterator  `Combinat.Permutations`  which  can  be  used  to  enumerate  the permutations of a large number.

```julia-repl
julia> permutations(3)
6-element Vector{Vector{Int64}}:
 [1, 2, 3]
 [1, 3, 2]
 [2, 1, 3]
 [2, 3, 1]
 [3, 1, 2]
 [3, 2, 1]

julia> sum(first(p) for p in Combinat.Permutations(5))
360
```
