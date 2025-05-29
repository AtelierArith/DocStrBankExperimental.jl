```
cycles(g::Perm)
```

Decompose permutation `g` into disjoint cycles.

Return a `CycleDec` object which iterates over disjoint cycles of `g`. The ordering of cycles is not guaranteed, and the order within each cycle is computed up to a cyclic permutation. The cycle decomposition is cached in `g` and used in future computation of `permtype`, `parity`, `sign`, `order` and `^` (powering).

# Examples

```jldoctest
julia> g = Perm([3,4,5,2,1,6])
(1,3,5)(2,4)

julia> collect(cycles(g))
3-element Vector{Vector{Int64}}:
 [1, 3, 5]
 [2, 4]
 [6]
```
