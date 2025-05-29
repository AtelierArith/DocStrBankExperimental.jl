```julia
getPoints(x)
getPoints(x, )

```

Return underlying points used to construct the [`ManifoldKernelDensity`](@ref).

Notes

  * Return type is `::Vector{P}` where `P` represents a Manifold point type (e.g. group element or coordinates).
  * Second argument controls whether partial dimensions only should be returned (`=true` default).

DevNotes

  * Currently converts down to manifold from matrix of coordinates (legacy), to be deprecated TODO
