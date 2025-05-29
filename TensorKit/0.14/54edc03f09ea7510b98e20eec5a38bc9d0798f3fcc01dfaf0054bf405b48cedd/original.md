```
fuse(V₁::S, V₂::S, V₃::S...) where {S<:ElementarySpace} -> S
fuse(P::ProductSpace{S}) where {S<:ElementarySpace} -> S
```

Return a single vector space of type `S` that is isomorphic to the fusion product of the individual spaces `V₁`, `V₂`, ..., or the spaces contained in `P`.
