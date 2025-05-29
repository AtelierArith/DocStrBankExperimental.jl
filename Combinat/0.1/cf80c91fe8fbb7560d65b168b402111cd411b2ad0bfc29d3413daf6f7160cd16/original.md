`compositions(n[,k];min=1)`, `ncompositions(n[,k];min=1)`

This  function returns the compositions of  `n` (the compositions of length `k`  if a second argument `k` is given), where a composition of the integer `n`  is a decomposition `n=p₁+…+pₖ` in  integers `≥min`, represented as the vector  `[p₁,…,pₖ]`. Unless `k` is given,  `min` must be `>0`. Compositions are sometimes called ordered partitions.

`ncompositions`  returns  (faster)  the  number  of compositions. There are $2^{n-1}$  compositions of `n` in  integers `≥1`, and `binomial(n-1,k-1)` compositions of `n` in `k` parts `≥1`.

```julia-repl
julia> ncompositions(4)
8

julia> compositions(4)
8-element Vector{Vector{Int64}}:
 [4]
 [1, 3]
 [2, 2]
 [3, 1]
 [1, 1, 2]
 [1, 2, 1]
 [2, 1, 1]
 [1, 1, 1, 1]

julia> ncompositions(4,2)
3

julia> compositions(4,2)
3-element Vector{Vector{Int64}}:
 [1, 3]
 [2, 2]
 [3, 1]

julia> ncompositions(4,2;min=0)
5

julia> compositions(4,2;min=0)
5-element Vector{Vector{Int64}}:
 [0, 4]
 [1, 3]
 [2, 2]
 [3, 1]
 [4, 0]
```

The compositions are implemented by an iterator `Combinat.Compositions(n[,k];min=1)`  which  can  be  used to enumerate the compositions of a large number.
