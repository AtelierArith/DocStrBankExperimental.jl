```
project!(M::AbstractManifold, q, p)
```

Project point `p` from the ambient space onto the [`AbstractManifold`](@ref) `M`. The result is storedin `q`. This method is only available for manifolds where implicitly an embedding or ambient space is given. Additionally, the projection includes changing data representation, if applicable, i.e. if the points on `M` are not represented in the same array data, the data is changed accordingly.

See also: [`EmbeddedManifold`](@ref), [`embed!`](@ref embed!(M::AbstractManifold, q, p))
