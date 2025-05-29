```
⊕(V₁::S, V₂::S, V₃::S...) where {S<:ElementarySpace} -> S
oplus(V₁::S, V₂::S, V₃::S...) where {S<:ElementarySpace} -> S
```

Return the corresponding vector space of type `S` that represents the direct sum sum of the spaces `V₁`, `V₂`, ... Note that all the individual spaces should have the same value for [`isdual`](@ref), as otherwise the direct sum is not defined.
