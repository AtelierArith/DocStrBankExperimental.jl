```
default_library(d::FullDim, ::Type{T}) where {T}
```

Returns the default polyhedral library for `d`-dimensional polyhedron of coefficient type `T`.

## Examples

To obtain the default library for 2-dimensional polyhedra of eltype `Float64`, do `default_library(2, Float64)`.

Given an `StaticArrays.SVector` `v`, to obtain a default library for points of the type of `v` in a type stable way, do `default_library(Polyhedra.FullDim(v), eltype(v))`.
