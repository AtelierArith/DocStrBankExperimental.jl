```
dimensionality(g::PeriodicGraph{N}) where N
```

Determine the actual dimension of each connected component of `g`. Return a dictionary where each entry `n => [(l1,m1), (l2,m2), ...]` means that `li` is a list of vertices that form a connected component of dimension `n`, and that component is present `mi` times per unit cell.

In other words, the connected component `li` has a periodicity that can only be expressed in a unit cell `mi` times larger than the current one. See also [`split_catenation`](@ref).

## Examples

```jldoctest
julia> dimensionality(PeriodicGraph("2   1 1  1 0   2 2  -1 1   3 3  1 0   3 3  0 1"))
Dict{Int64, Vector{Tuple{Vector{Int64}, Int64}}} with 2 entries:
  2 => [([3], 1)]
  1 => [([1], 1), ([2], 1)]

julia> dimensionality(PeriodicGraph("1   1 1  2"))
Dict{Int64, Vector{Tuple{Vector{Int64}, Int64}}} with 1 entry:
  1 => [([1], 2)]
```
