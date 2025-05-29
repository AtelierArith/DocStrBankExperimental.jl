```
isomorphism(::Type{T}, G::Group; on_gens=false) where T <: Group
```

Return an isomorphism from `G` to a group `H` of type `T`. An exception is thrown if no such isomorphism exists.

If `on_gens` is `true` then `gens(G)` is guaranteed to correspond to `gens(H)`; an exception is thrown if this is not possible.

Isomorphisms are usually cached in `G`, subsequent calls of `isomorphism` with the same `T` (and the same value of `on_gens`) yield identical results.

If only the image of such an isomorphism is needed, use `T(G)`; but this will assume `on_gens=false`.
