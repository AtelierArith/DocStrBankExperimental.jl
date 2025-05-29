```
number_of_coordinates(M::AbstractManifold, B::AbstractBasis)
number_of_coordinates(M::AbstractManifold, ::𝔾)
```

Compute the number of coordinates in basis of field type `𝔾` on a manifold `M`. This also corresponds to the number of vectors represented by `B`, or stored within `B` in case of a [`CachedBasis`](@ref).
