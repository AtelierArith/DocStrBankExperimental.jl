```
permtype(g::Perm)
```

Return the type of permutation `g`, i.e. lengths of disjoint cycles in cycle decomposition of `g`.

The lengths are sorted in decreasing order by default. `permtype(g)` fully determines the conjugacy class of `g`.

# Examples

```jldoctest
julia> g = Perm([3,4,5,2,1,6])
(1,3,5)(2,4)

julia> permtype(g)
3-element Vector{Int64}:
 3
 2
 1

julia> e = one(g)
()

julia> permtype(e)
6-element Vector{Int64}:
 1
 1
 1
 1
 1
 1
```
