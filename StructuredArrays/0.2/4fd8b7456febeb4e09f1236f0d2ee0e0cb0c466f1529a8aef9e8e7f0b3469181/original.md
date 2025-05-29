```
A = CartesianMeshArray(inds...; step, origin=nothing)
```

builds an abstract array `A` representing a `N`-dimensional Cartesian mesh with shape `inds...` and given `step` and `origin`. The syntax `A[i1,i2,...]` yields the coordinates of the node at index `(i1,i2,...)`. Node indices may also be specified as a tuple of `Int`s or as a `CartesianIndex`. The coordinates are lazily computed and the storage is `O(1)`.

Also see [`CartesianMesh`](@ref StructuredArrays.Meshes.CartesianMesh) for a description of arguments `step` and `origin`.
