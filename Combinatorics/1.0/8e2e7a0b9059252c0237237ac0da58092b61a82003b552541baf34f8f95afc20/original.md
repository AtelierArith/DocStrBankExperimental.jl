```
permutations(a, t)
```

Generate all size `t` permutations of an indexable object `a`. Only works for `a` with defined length.  If `(t <= 0) || (t > length(a))`, then returns an empty vector of eltype of `a`

# Examples

```jldoctest
julia> [ (len, permutations(1:3, len)) for len in -1:4 ]
6-element Vector{Tuple{Int64, Any}}:
 (-1, Vector{Int64}[])
 (0, [Int64[]])
 (1, [[1], [2], [3]])
 (2, Combinatorics.Permutations{UnitRange{Int64}}(1:3, 2))
 (3, Combinatorics.Permutations{UnitRange{Int64}}(1:3, 3))
 (4, Vector{Int64}[])

julia> [ (len, collect(permutations(1:3, len))) for len in -1:4 ]
6-element Vector{Tuple{Int64, Vector{Vector{Int64}}}}:
 (-1, [])
 (0, [[]])
 (1, [[1], [2], [3]])
 (2, [[1, 2], [1, 3], [2, 1], [2, 3], [3, 1], [3, 2]])
 (3, [[1, 2, 3], [1, 3, 2], [2, 1, 3], [2, 3, 1], [3, 1, 2], [3, 2, 1]])
 (4, [])
```
