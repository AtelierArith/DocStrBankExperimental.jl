```
permutations(a)
```

Generate all permutations of an indexable object `a` in lexicographic order. Because the number of permutations can be very large, this function returns an iterator object. Use `collect(permutations(a))` to get an array of all permutations. Only works for `a` with defined length.

# Examples

```jldoctest
julia> permutations(1:2)
Combinatorics.Permutations{UnitRange{Int64}}(1:2, 2)

julia> collect(permutations(1:2))
2-element Vector{Vector{Int64}}:
 [1, 2]
 [2, 1]

julia> collect(permutations(1:3))
6-element Vector{Vector{Int64}}:
 [1, 2, 3]
 [1, 3, 2]
 [2, 1, 3]
 [2, 3, 1]
 [3, 1, 2]
 [3, 2, 1]
```
