```
multiset_permutations(a, t)
```

Generate all permutations of size `t` from an array `a` with possibly duplicated elements.

# Examples

```jldoctest
julia> collect(permutations([1,1,1], 2))
6-element Vector{Vector{Int64}}:
 [1, 1]
 [1, 1]
 [1, 1]
 [1, 1]
 [1, 1]
 [1, 1]

julia> collect(multiset_permutations([1,1,1], 2))
1-element Vector{Vector{Int64}}:
 [1, 1]

julia> collect(multiset_permutations([1,1,2], 3))
3-element Vector{Vector{Int64}}:
 [1, 1, 2]
 [1, 2, 1]
 [2, 1, 1]
```
