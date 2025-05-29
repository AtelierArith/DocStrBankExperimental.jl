`partitions(set::AbstractVector[,k])`, `npartitions(set::AbstractVector[,k])`

the  set of all unordered  partitions (in `k` sets  if `k` is given) of the set  `set` (a  collection without  repetitions). `npartitions`  returns the number of unordered partitions.

An *unordered partition* of `set` is a set of pairwise disjoints sets whose union is equal to `set`, and is represented by a Vector of Vectors.

```julia-repl
julia> npartitions(1:3)
5

julia> partitions(1:3)
5-element Vector{Vector{Vector{Int64}}}:
 [[1, 2, 3]]
 [[1, 2], [3]]
 [[1, 3], [2]]
 [[1], [2, 3]]
 [[1], [2], [3]]

julia> npartitions(1:4,2)
7

julia> partitions(1:4,2)
7-element Vector{Vector{Vector{Int64}}}:
 [[1, 2, 3], [4]]
 [[1, 2, 4], [3]]
 [[1, 2], [3, 4]]
 [[1, 3, 4], [2]]
 [[1, 3], [2, 4]]
 [[1, 4], [2, 3]]
 [[1], [2, 3, 4]]
```

Note  that `unique(sort.(partitions(mset[,k])))`  is a  version which works for a multiset `mset`.
