```
nthperm!(a, k)
```

In-place version of [`nthperm`](@ref); the array `a` is overwritten.

# Examples

```jldoctest
julia> a = [1, 2, 3];

julia> collect(permutations(a))
6-element Vector{Vector{Int64}}:
 [1, 2, 3]
 [1, 3, 2]
 [2, 1, 3]
 [2, 3, 1]
 [3, 1, 2]
 [3, 2, 1]

julia> nthperm!(a, 3); a
3-element Vector{Int64}:
 2
 1
 3

julia> nthperm!(a, 4); a
3-element Vector{Int64}:
 1
 3
 2

julia> nthperm!(a, 0)
ERROR: ArgumentError: permutation k must satisfy 0 < k ≤ 6, got 0
[...]
```
