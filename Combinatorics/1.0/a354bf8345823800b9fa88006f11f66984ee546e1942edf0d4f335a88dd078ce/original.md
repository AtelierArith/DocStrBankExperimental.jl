```
nthperm(a, k)
```

Compute the `k`th lexicographic permutation of the vector `a`.

# Examples

```jldoctest
julia> collect(permutations([1,2]))
2-element Vector{Vector{Int64}}:
 [1, 2]
 [2, 1]

julia> nthperm([1,2], 1)
2-element Vector{Int64}:
 1
 2

julia> nthperm([1,2], 2)
2-element Vector{Int64}:
 2
 1

julia> nthperm([1,2], 3)
ERROR: ArgumentError: permutation k must satisfy 0 < k ≤ 2, got 3
[...]
```
