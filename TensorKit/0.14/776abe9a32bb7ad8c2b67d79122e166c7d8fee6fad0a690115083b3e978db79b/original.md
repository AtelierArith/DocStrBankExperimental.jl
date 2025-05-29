```
flip(V::S) where {S<:ElementarySpace} -> S
```

Return a single vector space of type `S` that has the same value of [`isdual`](@ref) as `dual(V)`, but yet is isomorphic to `V` rather than to `dual(V)`. The spaces `flip(V)` and `dual(V)` only differ in the case of [`GradedSpace{I}`](@ref).
