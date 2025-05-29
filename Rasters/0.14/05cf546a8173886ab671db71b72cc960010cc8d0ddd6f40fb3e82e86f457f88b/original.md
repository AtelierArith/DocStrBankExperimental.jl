```
mappedcrs(x)
```

Get the mapped coordinate reference system for the `Y`/`X` dims of an array.

In [`Projected`](@ref) lookup this is used to convert [`Selector`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Dimensions.Lookups.Selector) values form the mappedcrs defined projection to the underlying projection, and to show plot axes in the mapped projection.

In `Mapped` lookup this is the coordinate reference system of the index values. See [`setmappedcrs`](@ref) to set it manually.
