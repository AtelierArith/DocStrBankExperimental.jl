```
short_vectors(L::ZZLat, [lb = 0], ub, [elem_type = ZZRingElem]; check::Bool = true)
                                   -> Vector{Tuple{Vector{elem_type}, QQFieldElem}}
```

Return all tuples `(v, n)` such that $n = |v G v^t|$ satisfies `lb <= n <= ub`, where `G` is the Gram matrix of `L` and `v` is non-zero.

Note that the vectors are computed up to sign (so only one of `v` and `-v` appears).

It is assumed and checked that `L` is definite.

See also [`short_vectors_iterator`](@ref) for an iterator version.
