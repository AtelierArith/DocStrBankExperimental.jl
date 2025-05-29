```
close_vectors(L:ZZLat, v:Vector, [lb,], ub; check::Bool = false)
                                        -> Vector{Tuple{Vector{Int}}, QQFieldElem}
```

Return all tuples `(x, d)` where `x` is an element of `L` such that `d = b(v - x, v - x) <= ub`. If `lb` is provided, then also `lb <= d`.

If `filter` is not `nothing`, then only those `x` with `filter(x)` evaluating to `true` are returned.

By default, it will be checked whether `L` is positive definite. This can be disabled setting `check = false`.

Both input and output are with respect to the basis matrix of `L`.

# Examples

```jldoctest
julia> L = integer_lattice(matrix(QQ, 2, 2, [1, 0, 0, 2]));

julia> close_vectors(L, [1, 1], 1)
3-element Vector{Tuple{Vector{ZZRingElem}, QQFieldElem}}:
 ([2, 1], 1)
 ([0, 1], 1)
 ([1, 1], 0)

julia> close_vectors(L, [1, 1], 1, 1)
2-element Vector{Tuple{Vector{ZZRingElem}, QQFieldElem}}:
 ([2, 1], 1)
 ([0, 1], 1)
```
