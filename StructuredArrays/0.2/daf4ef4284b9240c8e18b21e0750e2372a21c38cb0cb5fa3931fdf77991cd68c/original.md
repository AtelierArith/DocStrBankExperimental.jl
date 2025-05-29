```
mesh = CartesianMesh{N}(step, origin = nothing)
```

yields a callable object that generates the coordinates of the nodes of a `N`-dimensional Cartesian mesh with given `step` between consecutive nodes and `origin` of coordinates. If any of `step` or `origin` is a `N`-tuple, the parameter `N` may be omitted. Calling the mesh object with `i = (i1,i2,...)`, the `N` indices of a node, yields:

```
mesh(i) = step .* i             # if `origin` is `nothing`
mesh(i) = step .* (i .- origin) # else
```

Thanks to broadcasting rules, each of `step` and `origin` may be specified as a scalar to assume that this parameters is the same for all dimensions, as a `N`-tuple otherwise. `origin` may also be `nothing` (the default), to assume that the origin of the mesh is at index `(0,0,...)`. In the implementation, the exact formula used to compute the coordinates of the nodes is optimized for the different possible cases. As a consequence, specifying `origin` as `0` or as a `N`-tuple of `0`s yields a mesh with the same coordinates but computed with more overheads than with `origin = nothing`.

`step` may have units (possibly different for each dimension) but `origin` must be unitless (integer or real). The values of the mesh parameters can be retrieved by calling `step(mesh)` or [`origin(mesh)`](@ref StructuredArrays.Meshes.origin). Call `step(Tuple,mesh)` or `origin(Tuple,mesh)` to retrieve a `N`-dimensional *step* and *origin* in all cases. The values of `step` and `origin` stored by the mesh may be converted at construction time to reduce the number of operations when computing coordinates. This optimization assumes that all indices are specified as `Int`s but fractional indices (i.e. reals) are also accepted.

A typical usage is to wrap a Cartesian mesh in a `StructuredArray` to build an abstract array whose values are the coordinates of the nodes of a finite size Cartesian mesh. For example:

```
grid = StructuredArray(CartesianMesh{N}(step, origin), inds...)
```

with `inds...` the *shape* (indices and/or dimensions) of the mesh. This can also be done by calling [`CartesianMeshArray`](@ref StructuredArrays.Meshes.CartesianMeshArray):

```
grid = CartesianMeshArray(inds...; step, origin=nothing)
```
