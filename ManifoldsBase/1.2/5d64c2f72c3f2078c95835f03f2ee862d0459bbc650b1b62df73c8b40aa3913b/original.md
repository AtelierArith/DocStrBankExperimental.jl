```
project(M::AbstractManifold, p)
```

Project point `p` from the ambient space of the [`AbstractManifold`](@ref) `M` to `M`. This method is only available for manifolds where implicitly an embedding or ambient space is given. Additionally, the projection includes changing data representation, if applicable, i.e. if the points on `M` are not represented in the same array data, the data is changed accordingly.

See also: [`EmbeddedManifold`](@ref), [`embed`](@ref embed(M::AbstractManifold, p))
