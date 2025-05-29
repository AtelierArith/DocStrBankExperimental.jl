```
DimTree
```

A nested tree of dimensional arrays.

Still in expermental stage: breaking changes may occurr without  a major version bump to DimensionalData. Please report any issues and  feedback on GitHub to push this towards a stable implementation.

`DimTree` is loosely typed and based on `OrderedDict` rather than `NamedTuple` of `DimStack`, so it is slower to index but very fast to compile, and very flexible.

Trees can be nested indefinately, branches inheriting dimensions from the tree. 

# Getting and setting layers and branches

Local layers are accessed with `getindex` and a `Symbol`, returning a `DimArray`, e.g. `dt[:layer]` or a `DimStack` with `dt[(:layer1, :layer2)]`. 

Branches are accessed with `getproperty`, e.g. `dt.branch`. 

Layers and branches can be set with `setindex!` and `setproperty!` respectively.

## Dimensions and branches

Dimensions that are shared with the base of the tree must be identical. They are stored at the base level of the tree that they are used in,  and propagate out to branches.

Within a branch, all layers use a subset of the dimensions available to the branch.

Accross branches, there may be versions of the same dimensions with  different lookup values. These may cover different extents, resolutions,  or whatever properties of lookups are required to vary.

This property can be used for tiles with differen X/Y extents or pyramid layers with different resolutions, for example.

## Example

`julia xdim, ydim = X(1:10), Y(1:15),  z1, z2 = Z([:a, :b, :c]), Z([:d, :e, :f]) a = rand(xdim, ydim) b = rand(Float32, xdim, ydim) c = rand(Int, xdim, ydim, z1) d = rand(Int, xdim, z2) DimTree(a, b)``
