```
SymmetryGroup3D{T} <: PeriodicGraphs.AbstractSymmetryGroup
```

Store the information on the symmetry operations available on a [`PeriodicGraphEmbedding3D`](@ref).

`T` is the numeric type parameter of each individual [`PeriodicSymmetry3D`](@ref), which can be obtained by iterating over the `SymmetryGroup3D`. For example, if `symms` is a `SymmetryGroup3D{Rational{Int}}`, then `first(symms)` will be a `PeriodicSymmetry3D{Rational{Int64}}`. `collect(symms)` gives the full list of symmetries stored in the `SymmetryGroup3D`.

The list of the symmetrically-unique vertices of the `PeriodicGraphEmbedding3D` can be retrieved by calling `unique(symms)`. The mapping between any vertex `i` and its corresponding unique vertex can be obtained by calling `symms` itself with the vertex, like `symms(i)`.
