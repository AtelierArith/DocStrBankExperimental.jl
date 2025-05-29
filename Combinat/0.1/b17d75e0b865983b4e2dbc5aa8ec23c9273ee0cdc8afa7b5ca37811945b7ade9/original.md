`partitions(n::Integer[,k])`, `npartitions(n::Integer[,k])`

`partitions`  returns in lexicographic order the partitions (with `k` parts if  `k`  is  given)  of  the  positive  integer `n` . `npartitions` returns (faster) the number of partitions.

There are approximately `exp(π√(2n/3))/(4√3 n)` partitions of `n`.

A   *partition*  is   a  decomposition   `n=p₁+p₂+…+pₖ`  in  integers  with `p₁≥p₂≥…≥pₖ>0`, and is represented by the vector `p=[p₁,p₂,…,pₖ]`. We write `p⊢n` to say that `p` is a partition of `n`.

```julia-repl
julia> npartitions(7)
15

julia> partitions(7)
15-element Vector{Vector{Int64}}:
 [1, 1, 1, 1, 1, 1, 1]
 [2, 1, 1, 1, 1, 1]
 [2, 2, 1, 1, 1]
 [2, 2, 2, 1]
 [3, 1, 1, 1, 1]
 [3, 2, 1, 1]
 [3, 2, 2]
 [3, 3, 1]
 [4, 1, 1, 1]
 [4, 2, 1]
 [4, 3]
 [5, 1, 1]
 [5, 2]
 [6, 1]
 [7]

julia> npartitions(7,3)
4

julia> partitions(7,3)
4-element Vector{Vector{Int64}}:
 [3, 2, 2]
 [3, 3, 1]
 [4, 2, 1]
 [5, 1, 1]
```

The  partitions are implemented by an iterator `Combinat.Partitions(n[,k])` which can be used to enumerate the partitions of a large number.
