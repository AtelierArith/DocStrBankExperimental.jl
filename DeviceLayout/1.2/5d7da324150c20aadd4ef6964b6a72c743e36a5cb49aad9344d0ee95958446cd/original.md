```
GeometryEntity{T <: Coordinate}
```

A geometric entity that can be placed in a coordinate system.

New concrete `GeometryEntity` subtypes must implement the following:

```julia
to_polygons(::MyEntity)
transform(ent::MyEntity, f)
```

A subtype may also implement specialized transformations like `transform(::MyEntity, ::ScaledIsometry)`, for example if special handling is possible for angle-preserving transformations, as well as specializations for

```
magnify
rotate
rotate90
reflect_across_xaxis
translate
```

which otherwise construct the corresponding `ScaledIsometry` and call `transform`.

New subtypes may also implement

```julia
footprint
halo
lowerleft
upperright
```

if there are better ways to calculate these than with `to_polygons` (the default), which may be slow and expensive. The bounding rectangle returned by `bounds` is derived from `lowerleft` and `upperright`. By default, `halo` is derived from `footprint` and `offset`.

New subtypes may also implement any application functions required for valid styles. Not all styles need be valid for any given entity type.
