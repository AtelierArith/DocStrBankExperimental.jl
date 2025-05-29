```
⊗(V₁::S, V₂::S, V₃::S...) where {S<:ElementarySpace} -> S
```

Create a [`ProductSpace{S}(V₁, V₂, V₃...)`](@ref) representing the tensor product of several elementary vector spaces. For convience, Julia's regular multiplication operator `*` applied to vector spaces has the same effect.

The tensor product structure is preserved, see [`fuse`](@ref) for returning a single elementary space of type `S` that is isomorphic to this tensor product.
