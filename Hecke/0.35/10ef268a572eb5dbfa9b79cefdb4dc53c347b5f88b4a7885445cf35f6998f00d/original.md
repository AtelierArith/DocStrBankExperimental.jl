```
shortest_vectors(L::ZZLat, [elem_type = ZZRingElem]; check::Bool = true)
                                           -> QQFieldElem, Vector{elem_type}, QQFieldElem}
```

Return the list of shortest non-zero vectors in absolute value. Note that the vectors are computed up to sign (so only one of `v` and `-v` appears).

It is assumed and checked that `L` is definite.

See also [`minimum`](@ref).
